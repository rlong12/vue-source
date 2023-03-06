<script setup>
</script>

<template>
  <h1>HTML Forms</h1>
  <form class="form-example">
    <div class="form-example">
        <label for="name">Enter your name:</label>
        <input type="text" name="name" id="name">
    </div>
    <div class="form-example">
        <label for="search">Search</label>
        <input type="search" name="search" id="search">
    </div>
    <div class="form-example">
        <label for="email">Email</label>
        <input type="email" name="email" id="email" placeholder="test@example.com">
    </div>
    <div class="form-example">
        <label for="tel">Telephone</label>
        <input type="tel" name="tel" id="tel" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}">
    </div>
    <div class="form-example">
        <label for="url">URL</label>
        <input type="url" name="url" id="url" placeholder="https://example.com">
    </div>
    <div class="form-example">
        <label for="pass">Enter Password:</label>
        <input type="password" name="pass" id="pass" minlength="8">
    </div>
    <div class="form-example">
        <label for="address">Enter your address:</label>
        <textarea name="name" id="address" rows="3" cols="20"></textarea>
    </div>
    <fieldset class="checkboxes">
        <legend>Choose flavors you like:</legend>
        <div class="form-example">
            <input type="checkbox" id="chocolate" name="vanilla">
            <label for="chocolate">chocolate</label>
        </div>
        <div class="form-example">
            <input type="checkbox" id="vanilla" name="vanilla">
            <label for="vanilla">vanilla</label>
        </div>
    </fieldset>
    <fieldset class="choice">
        <legend>Yes or No?</legend>
        <div class="form-example">
            <input type="radio" id="yes" name="choice" value="yes" checked>
            <label for="yes">Yes</label>
        </div>
        <div class="form-example">
            <input type="radio" id="no" name="choice" value="no">
            <label for="no">No</label>
        </div>
    </fieldset>
    <div class="datalists">
        <label for="icecream-choice">Choose a flavor:</label>
        <input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice">

        <datalist id="ice-cream-flavors">
            <option value="Chocolate"></option>
            <option value="Vanilla"></option>
            <option value="Strawberry"></option>
        </datalist>
    </div>
    <div class="form-example">
        <label for="tentacles">Number of tentacles:</label>
        <input type="number" id="tentacles" name="tentacles" min="10" max="100">
    </div>
    <div class="form-example">
        <input type="range" id="volume" name="volume" min="0" max="100">
        <label for="volume">Volume</label>
    </div>
    <div class="form-example">
        <label for="file">File Progress:</label>
        <progress id="file" max="100" value="65">65%</progress>
    </div>
    <div class="form-example">
        <label for="fuel">Fuel level:</label>
        <meter id="fuel" min="0" max="100" low="33" high="66" optimum="80" value="64">at 64/100</meter>
    </div>
    <div class="form-example">
        <label for="start">Start date:</label>
        <input type="date" id="start" name="trip-start" value="2020-07-08" min="2018-01-01" max="2018-12-31">
    </div>
    <div class="form-example">
        <label for="appt">Choose a time:</label>
        <input type="time" id="appt" name="appt" min="09:00" max="18:00">
    </div>
    <div class="form-example">
        <label for="meeting-time">Choose a time for your appointment:</label>
        <input type="datetime-local" id="meeting-time" name="meeting-time" value="2018-04-12T19:30" min="2018-04-07T00:00" max="2018-04-14T00:00">
    </div>
    <div class="form-example">
        <div class="color-picker">
            <input type="color" id="primary" name="primary" value="#e66465">
            <label for="primary">Primary</label>
        </div>
        <div class="color-picker">
            <input type="color" id="secondary" name="secondary" value="#f6b73c">
            <label for="secondary">Secondary</label>
        </div>
    </div>
    <div class="form-example">
        <label for="file">Choose pic(png):</label>
        <input type="file" id="file" name="file" accept="image/png">
    </div>
    <div class="form-example">
        <input type="submit" value="Submit">
    </div>
    <div class="form-example">
        <label for="id">User ID:</label>
        <input type="text" id="id" name="id">

        <input type="reset" value="Reset">
        <input type="submit" value="Submit">
    </div>
    <div class="form-example">
        <input type="button" value="Click Me">
    </div>
    <div class="form-example">
        <input type="hidden" id="postID" name="postID" value="12">
    </div>
  </form>
</template>

<style>

</style>
