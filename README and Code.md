Weather-App
===========
require 'weather'
require 'sinatra'
def get_weather(location)
	client = Weather::Client.new
	client.lookup_by_location(location).condition['text']
end

def get_temp(location)
	client = Weather::Client.new
	farenheit = client.lookup_by_location(location).condition['temp']
end
 
post '/weather' do
    post = params[:post]['location']

    @weather = get_weather(post)
	erb :home
end


    "#{@weather}"
    
    if (@weather == 'sunny')
        erb :sunny
    elsif (@weather == 'cloudy')
        erb :cloudy
    elsif (@weather == 'snowy')
        erb :snowy
    else
        erb :default
    end
end

<html>
<head>
<meta charset = "utf-8">
<title>Weather or Not</title>
<link href='http://fonts.googleapis.com/css?family=Vollkorn' rel='stylesheet' type='text/css'>
</head>
<body>

<body id = "cloudy"
<h1>Cloudy
<p> and <%= @temp %>&deg; F</p>
</h1>

<body id = "sunny"
<h1>Sunny
<p> and <%= @temp %>&deg; F</p>
</h1>

<body id = "rainy"
<h1>Rainy
<p> and <%= @temp %>&deg; F</p>
</h1>

<body id = "snowy"
<h1>Snow
<p> and <%= @temp %>&deg; F</p>
</h1>

<body id = "fog"
<h1>Foggy
<p> and <%= @temp %>&deg; F</p>
</h1>

<body id = "default"
<h1>Sorry, the elves don't know what the weather is here
<p> and <%= @temp %>&deg; F</p>
</h1>



<%= yield %>
</head>
</body>
<form method="post" action="/weather">
	Enter your location: <input type="text" name="post[location]" />
	<input type="submit" name="Search" />
</form>
