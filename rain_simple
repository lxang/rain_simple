function rain(area_div, material, density, speed){
		var self = {};

		if(typeof area_div == "undefined" || area_div.nodeType != 1){
			alert("please get me an area element where you want to rain");
			return self;
		}
		if(typeof material == "undefined" || material.nodeType != 1){
			alert("please get me the material element that you want to rain");
			return self;
		}

		var area_width;
		var area_height;
		var material_width;
		var material_height;
		var start_pos_top;
		var start_opcatiy;

		var init = function(area_div, material, density, speed){
			$.extend(self, {
				area_div:$(area_div),
				material:$(material).hide(),
				density:density,
				speed:speed,
				timer: false
			});

			area_width 		= $(area_div).width();
			area_height 	= $(area_div).height();
			material_width 	= $(material).width();
			material_height = $(material).height();
			start_pos_top 	= -material_height;
			start_opcatiy 	= 0.5 + Math.random();

			if(self.area_div.css("position") == "static"){
				self.area_div.css({
					position: "relative",
					overflow:"hidden",
					top:0,
					left:0,
				});
			}


			self.material.css({
				position: "absolute",
				display:"none"
			});

			var xxLen = self.density;

			for(var i = 0; i < xxLen; i++){
				self.material.clone().appendTo(self.area_div);
			}
		}

		self.active = function(){
			var start_pos_left = Math.abs(Math.random() * area_width - material_width);
			var end_pos_top = area_height - material_height*[Math.random()+1];
			var end_pos_left = start_pos_left + Math.random()*material_width*2 - material_width;
			var durationFall = !isNaN(parseFloat(self.speed))? self.speed : area_height*10 + Math.random()*500;

			if(typeof rain_timer != "undefined"){
				clearTimeout(self.timer);
			}

			self.area_div.children("#" + self.material.attr("id")).not(self.material).not(":visible").first().show()
				.css({
					top: start_pos_top,
					left: start_pos_left,
					opacity: start_opcatiy,
				}).animate({
					top: end_pos_top,
					left: end_pos_left,
					opacity: 1
				}, durationFall, 'swing', function(){
					$(this).hide();
				});

			self.timer = setTimeout(function(){
				self.active();
			}, Math.ceil(self.speed/self.density));
		}
		self.start = function(){
			self.active();
		}
		self.pasue = function(){
			self.stop();
			self.area_div.children(self.material).stop();
		}
		self.stop = function(){
			clearTimeout(self.timer);
		}
		self.setSpeed = function(speed){
			self.speed = speed;
		}
		self.setDensity = function(density){
			self.density = density;
		}

		init(area_div, material, density, speed);
		return self;
	}
