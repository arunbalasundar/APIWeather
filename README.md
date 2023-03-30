# APIWeather
Few Requests for Weather API using Postman

# URL
https://samples.openweathermap.org/data/2.5/weather?q=London,uk&appid=b6 907d289e10d714a6e88b30761fae22

# Tests

let responseJson = pm.response.json();
pm.test("Latitude is correct", function() {
    pm.expect(responseJson.coord.lat).to.eql(51.51);
});
pm.test("Longitude is correct", function() {
    pm.expect(responseJson.coord.lon).to.eql(-0.13);
});
pm.test("Temperature is within range", function() {
    pm.expect(responseJson.main.temp).to.be.within(0, 300);
});
pm.test("Valid city name", function() {
    pm.expect(responseJson.name).to.eql("London");
});
pm.test("Weather conditions", function() {
    pm.expect(responseJson.weather[0].main).to.eql("Drizzle");
});

