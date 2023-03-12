
[JS Classes | The Coding Train - Topics in ES6](https://thecodingtrain.com/tracks/topics-in-native-javascript/code/6-objects/2-classes)


```JavaScript
// Note PascalCase naming
class Bubble {

	constructor(x, y, radius) {
		this.x = x;
		this.y = y;
    this.radius = radius;
		this.alpha = 255;
	}

	draw() {
		stroke(255, this.alpha);
		noFill();
		circle(this,x, this.y, this.r);
	}

	grow() {
		this.r += 1;
  }

	fade() {
		this.alpha -= 5;
  }
	
}

let bubble = new Bubble();
```