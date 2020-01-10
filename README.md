layui.use('laydate', function() {
				var laydate = layui.laydate;

				//执行一个laydate实例
				laydate.render({
					elem: '#test1' //指定元素
						,
					format: 'yyyy-MM-dd',
					trigger: 'click'
				});

			});
			layui.use(['form', 'layer', 'admin'], function() {
						var form = layui.form,
							admin = layui.admin,
							layer = layui.layer;
						form.render();
						$(document).ready(function() {
							$.ajax({
								type: 'get',
								url: getPath() + '/house/findAll',
								data: {
									id: '0'
								},
								async: false,
								dataType: "json",
								success: function(data) {
									console.log('data', data)
									if (data.code == 200) {
										for (var i = 0; i < data.data.length; i++) {
											//先创建好select里面的option元素
											var option = document.createElement("option");
											//转换DOM对象为JQ对象,好用JQ里面提供的方法 给option的value赋值
											$(option).val(data.data[i].id);
											//给option的text赋值,这就是你点开下拉框能够看到的东西
											$(option).text(data.data[i].title);
											//获取select 下拉框对象,并将option添加进select
											$('#one').append(option);
											form.render('select');
											console.log(option)
										}
									} else {
										console.log('data', data)
									}
								},
								error: function(data) {
									console.log('data``````````````````````````', data)
								},

							});
						})

						//一级分类触发，加载二级分类
						form.on('select(one)', function(data) {
							var objS = document.getElementById("one");
							var place = objS.options[objS.selectedIndex].value;
							console.log(place)
							//查询所有二级分类
							$.ajax({
								type: 'get',
								url: getPath() + '/house/findAll',
								data: {
									id: place,
								},
								dataType: "json",
								success: function(data) {
									console.log(data)
									if (data.code == 200) {
										$("#two").empty();
										$('#two').append("<option value=''>请选择所属二级分类</option>");
										form.render('select');
										for (var i = 0; i < data.data.length; i++) {
											//先创建好select里面的option元素
											var option = document.createElement("option");
											//转换DOM对象为JQ对象,好用JQ里面提供的方法 给option的value赋值
											$(option).val(data.data[i].id);
											//给option的text赋值,这就是你点开下拉框能够看到的东西
											$(option).text(data.data[i].title);
											//获取select 下拉框对象,并将option添加进select
											$('#two').append(option);
											form.render('select');
											console.log(option)
										}
									} else {
										console.log('data', data)
										//layer.msg(data.msg)
									}
								},
								error: function(data) {
									console.log('data``````````````````````````', data)
								},

							});
						})
						//二级分类触发，加载三级分类
						form.on('select(two)', function(data) {
							var objS = document.getElementById("two");
							var place = objS.options[objS.selectedIndex].value;
							console.log(place)
							//查询所有三级分类
							$.ajax({
								type: 'get',
								url: getPath() + '/house/findAll',
								data: {
									id: place,
								},

								dataType: "json",
								success: function(data) {
									console.log(data)
									if (data.code == 200) {
										$("#three").empty();
										$('#three').append("<option value=''>请选择所属三级分类</option>");
										form.render('select');
										for (var i = 0; i < data.data.length; i++) {
											//先创建好select里面的option元素
											var option = document.createElement("option");
											//转换DOM对象为JQ对象,好用JQ里面提供的方法 给option的value赋值
											$(option).val(data.data[i].id);
											//给option的text赋值,这就是你点开下拉框能够看到的东西
											$(option).text(data.data[i].title);
											//获取select 下拉框对象,并将option添加进select
											$('#three').append(option);
											form.render('select');
											console.log(option)
										}
									} else {
										console.log('data', data)
										//layer.msg(data.msg)
									}
								},
								error: function(data) {
									console.log('data``````````````````````````', data)
								},

							});
						})
						//三级分类触发，加载四级分类
						form.on('select(three)', function(data) {
							var objS = document.getElementById("three");
							var place = objS.options[objS.selectedIndex].value;
							console.log(place)
							//查询所有三级分类
							$.ajax({
								type: 'get',
								url: getPath() + '/house/findAll',
								data: {
									id: place,
								},
								dataType: "json",
								success: function(data) {
									console.log(data)
									if (data.code == 200) {
										$("#four").empty();
										$('#four').append("<option value=''>请选择所属四级分类</option>");
										form.render('select');
										for (var i = 0; i < data.data.length; i++) {
											//先创建好select里面的option元素
											var option = document.createElement("option");
											//转换DOM对象为JQ对象,好用JQ里面提供的方法 给option的value赋值
											$(option).val(data.data[i].id);
											//给option的text赋值,这就是你点开下拉框能够看到的东西
											$(option).text(data.data[i].title);
											//获取select 下拉框对象,并将option添加进select
											$('#four').append(option);
											form.render('select');
											console.log(option)
										}
									} else {
										console.log('data', data)
										//layer.msg(data.msg)
									}
								},
								error: function(data) {
									console.log('data``````````````````````````', data)
								},

							});
						})
						//四级分类触发，加载五级分类
						form.on('select(four)', function(data) {
							var objS = document.getElementById("four");
							var place = objS.options[objS.selectedIndex].value;
							// alert(place)
							//查询所有三级分类
							$.ajax({
								type: 'get',
								url: getPath() + '/house/findAll',
								data: {
									id: place,
								},
								dataType: "json",
								success: function(data) {
									console.log(data)
									if (data.code == 200) {
										$("#five").empty();
										$('#five').append("<option value=''>请选择所属五级分类</option>");
										form.render('select');
										for (var i = 0; i < data.data.length; i++) {
											//先创建好select里面的option元素
											var option = document.createElement("option");
											//转换DOM对象为JQ对象,好用JQ里面提供的方法 给option的value赋值
											$(option).val(data.data[i].id);
											//给option的text赋值,这就是你点开下拉框能够看到的东西
											$(option).text(data.data[i].title);
											//获取select 下拉框对象,并将option添加进select
											$('#five').append(option);
											form.render('select');
											console.log(option)
										}
									} else {
										console.log('data', data)
										//layer.msg(data.msg)
									}
								},
								error: function(data) {
									console.log('data``````````````````````````', data)
								},

							});
						})

						//五级分类触发，加载六级分类  
						form.on('select(five)', function(data) {
							var objS = document.getElementById("five");
							var place = objS.options[objS.selectedIndex].value;
							console.log(place)
							//查询所有三级分类
							$.ajax({
								type: 'get',
								url: getPath() + '/house/findAll',
								data: {
									id: place,

								},
								dataType: "json",
								success: function(data) {
									console.log(data)
									if (data.code == 200) {
										$("#six").empty();
										$('#six').append("<option value=''>请选择所属六级分类</option>");
										form.render('select');
										for (var i = 0; i < data.data.length; i++) {
											//先创建好select里面的option元素
											var option = document.createElement("option"); //这边是添加的dom
											//转换DOM对象为JQ对象,好用JQ里面提供的方法 给option的value赋值
											$(option).val(data.data[i].id);
											//给option的text赋值,这就是你点开下拉框能够看到的东西
											$(option).text(data.data[i].title);
											//获取select 下拉框对象,并将option添加进select
											$('#six').append(option);
											form.render('select');
											console.log(option)

										}
									} else {
										console.log('data', data)
										//layer.msg(data.msg)
									}
								},
								error: function(data) {
									console.log('data``````````````````````````', data)
								},

							});
						})
