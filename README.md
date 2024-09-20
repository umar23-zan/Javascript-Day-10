# Javascript-Day-10
17a. Let's practice OOP by creating a class that represents a car.

Create a new file data/car.js, and create a class Car {}

Give the Car class 2 properties: brand and model. Then, create a

constructor that sets these 2 properties. Keep all properties public for now (we'll learn why in a later exercise).

Use this class to generate a few car objects:

{brand: 'Toyota', model: 'Corolla' }

{brand: 'Tesla', model: 'Model 3' }

console.log the car objects.

In checkout.js, load data/car.js using the import '...'; syntax, and check the console.
```
class Car {
  brand;
  model;

  constructor(carDetails) {
    this.brand = carDetails.brand;
    this.model = carDetails.model;
  }
}

const car1 = new Car({
  brand: 'Toyota',
  model: 'Corolla'
});
const car2 = new Car({
  brand: 'Tesla',
  model: 'Model 3'
});

console.log(car1);
console.log(car2);
```
17b. Add a method displayInfo() that console.logs $(brand) ${model) Run.displayInfo() for each car, and check the console.
```
displayInfo() {
    console.log(`${this.brand} ${this.model}`);
  }

console.log(car2);

car1.displayInfo();
car2.displayInfo();
```
17c. Add a speed property, which represents how fast the car is going. The speed should start at 0.
• Add 2 methods ao() (increases speed by 5) and brake() (decreases
speed by 5).
The speed should be limited between 0 and 200. Update displayInfo() to display the speed at the end:
`${brand} ${model), Speed: ${speed} km/h Call go() and brake() a few times for each car, call displayInfo() and
check the console to confirm the code is working.
```
speed = 0;

  constructor(carDetails) {
    this.brand = carDetails.brand;
    this.model = carDetails.model;
console.log(
      `${this.brand} ${this.model}, Speed: ${this.speed} km/h`
    );
  }

  go() {
    this.speed += 5;

    // Limit the speed to 200.
    if (this.speed > 200) {
      this.speed = 200;
    }
  }

  brake() {
    this.speed -= 5;

    // Limit the speed to 0.
    if (this.speed < 0) {
      this.speed = 0;
    }
car1.go();
car1.go();
car1.go();
car1.brake();
car1.displayInfo();

car2.displayInfo();
car2.go();
car2.brake();
car2.brake();
car2.displayInfo();
```
17d. Add isTrunkopen property, which tracks if the car's trunk is open. Should be a boolean property (true = open, false = closed).
Create openTrunk() and closeTrunk(), which opens / closes the trunk.
openTrunk() should not work if the car is moving.
go() should not work if the trunk is open.
Update displayInfo() to display trunk info at the end. Try the code.
```
isTrunkOpen = false;

  displayInfo() {
    const trunkStatus = this.isTrunkOpen ? 'open' : 'closed';

   

  go() {
   
    if (!this.isTrunkOpen) {
      this.speed += 5;
    }


  openTrunk() {
    if (this.speed === 0) {
      this.isTrunkOpen = true;
    }
  }

  closeTrunk() {
    this.isTrunkOpen = false;
  }
}


car1.openTrunk();
car1.displayInfo();

car2.displayInfo();
car2.go();
car2.brake();
car2.brake();
car2.displayInfo();


car2.openTrunk();

car2.go();
car2.displayInfo();
```
17e. Create a new class Racecar which extends car.
Race cars go faster than normal cars, so the RaceCar has an additional property acceleration. When using go(), increase the speed by acceleration instead of 5, and update the top speed to 300.
Race cars do not have a trunk. Update openTrunk() and closeTrunk() Create a race car { brand: 'McLaren', model: 'F1', acceleration: 20 and try the code.
```
class RaceCar extends Car {
  acceleration;

  constructor(carDetails) {
    super(carDetails);
    this.acceleration = carDetails.acceleration;
  }

  go() {
    this.speed += this.acceleration;

    if (this.speed > 300) {
      this.speed = 300;
    }
  }

  openTrunk() {
    console.log('Race cars do not have a trunk.');
  }

  closeTrunk() {
    console.log('Race cars do not have a trunk.');
  }
}

const raceCar = new RaceCar({
  brand: 'McLaren',
  model: 'F1',
  acceleration: 20
});

car2.displayInfo();

raceCar.go();
raceCar.go();
raceCar.go();
raceCar.displayInfo();
raceCar.openTrunk();
raceCar.displayInfo();
raceCar.brake();
raceCar.displayInfo();
```
17f. Make brand and model properties private (just like in real life, we
should not be able to change the brand and model of a car!) Update displayInfo() with the private properties, and try the code.
```
 #brand;
  #model;
this.#brand = carDetails.brand;
    this.#model = carDetails.model;
`${this.#brand} ${this.#model}, Speed: ${this.speed} km/h, Trunk: ${trunkStatus}`
```
17g. In the Amazon project, create a class Appliance {}
• An appliance is a specific type of product (it extends Product).
It has 2 extra properties: instructionsLink and warrantyLink. In the products array, add type, instructionsLink, and warrantyLink to the toaster (4th product). If you need, download the images from: supersimple.dev/images/appliance-instructions.png
supersimple.dev/images/appliance-warranty.png Convert the toaster into an Appliance class instead of a Product class.
★★★★★ 2197
$18.99
1
Instructions
Warranty
When displaying extra info, display the instructions and the warranty. Follow the design on the right: Find other products that are appliances (kettle, blender, etc.) and convert them to Appliance class.
```
class Appliance extends Product {
  instructionsLink;
  warrantyLink;

  constructor(productDetails) {
    super(productDetails);
    this.instructionsLink = productDetails.instructionsLink;
    this.warrantyLink = productDetails.warrantyLink;
  }

  extraInfoHTML() {
    return `
      <a href="${this.instructionsLink}" target="_blank">
        Instructions
      </a>
      <a href="${this.warrantyLink}" target="_blank">
        Warranty
      </a>
    `;
  }
}
type: 'appliance',
    instructionsLink: 'images/appliance-instructions.png',
    warrantyLink: 'images/appliance-warranty.png'

type: 'appliance',
    instructionsLink: 'images/appliance-instructions.png',
    warrantyLink: 'images/appliance-warranty.png'
```
17h. Create tests for the Product, Clothing, and Appliance classes.
Create a new test file data/productsTest.js and load it in tests.html
Create a test suite for each class and create tests for each class. (Export the classes, generate objects using each class, and check if the properties and methods are correct).
```
export class Product {
  id;
  image;
  name;
 }

import {Product, Clothing, Appliance} from '../../data/products.js';

describe('test suite: Product', () => {
  let product;

  beforeEach(() => {
    product = new Product({
      id: "e43638ce-6aa0-4b85-b27f-e1d07eb678c6",
      image: "images/products/athletic-cotton-socks-6-pairs.jpg",
      name: "Black and Gray Athletic Cotton Socks - 6 Pairs",
      rating: {
        stars: 4.5,
        count: 87
      },
      priceCents: 1090,
      keywords: [
        "socks",
        "sports",
        "apparel"
      ]
    });
  });

  it('has the correct properties', () => {
    
    expect(product.id).toEqual('e43638ce-6aa0-4b85-b27f-e1d07eb678c6');
    expect(product.image).toEqual('images/products/athletic-cotton-socks-6-pairs.jpg');
    expect(product.name).toEqual('Black and Gray Athletic Cotton Socks - 6 Pairs');
    expect(product.rating).toEqual({
      stars: 4.5,
      count: 87
    });
    expect(product.priceCents).toEqual(1090);
  });

  it('gets the stars url', () => {
    expect(product.getStarsUrl()).toEqual('images/ratings/rating-45.png');
  });

  it('gets the price', () => {
    expect(product.getPrice()).toEqual('$10.90');
  });

  it('does not display any extra info', () => {
    expect(product.extraInfoHTML()).toEqual('');
  });
});

describe('test suite: Clothing', () => {
  let clothing;

  beforeEach(() => {
    clothing = new Clothing({
      id: "83d4ca15-0f35-48f5-b7a3-1ea210004f2e",
      image: "images/products/adults-plain-cotton-tshirt-2-pack-teal.jpg",
      name: "Adults Plain Cotton T-Shirt - 2 Pack",
      rating: {
        stars: 4.5,
        count: 56
      },
      priceCents: 799,
      keywords: [
        "tshirts",
        "apparel",
        "mens"
      ],
      type: "clothing",
      sizeChartLink: "images/clothing-size-chart.png"
    });
  });

  it('has the correct properties', () => {
   
    expect(clothing.id).toEqual('83d4ca15-0f35-48f5-b7a3-1ea210004f2e'),
    expect(clothing.image).toEqual('images/products/adults-plain-cotton-tshirt-2-pack-teal.jpg');

    expect(clothing.sizeChartLink).toEqual('images/clothing-size-chart.png');
  });

  it('gets the stars url', () => {
    expect(clothing.getStarsUrl()).toEqual('images/ratings/rating-45.png');
  });

  it('gets the price', () => {
    expect(clothing.getPrice()).toEqual('$7.99');
  });

  it('displays a size chart link in extraInfoHTML', () => {
    
    expect(clothing.extraInfoHTML()).toContain(
      `<a href="images/clothing-size-chart.png" target="_blank">`
    );

    
    expect(clothing.extraInfoHTML()).toContain('Size chart');
  });
});

describe('test suite: Appliance', () => {
  let appliance;

  beforeEach(() => {
    appliance = new Appliance({
      id: "54e0eccd-8f36-462b-b68a-8182611d9add",
      image: "images/products/black-2-slot-toaster.jpg",
      name: "2 Slot Toaster - Black",
      rating: {
        stars: 5,
        count: 2197
      },
      priceCents: 1899,
      keywords: [
        "toaster",
        "kitchen",
        "appliances"
      ],
      type: 'appliance',
      instructionsLink: 'images/appliance-instructions.png',
      warrantyLink: 'images/appliance-warranty.png'
    });
  });

  it('has the correct properties', () => {
    expect(appliance.id).toEqual('54e0eccd-8f36-462b-b68a-8182611d9add'),
    expect(appliance.image).toEqual('images/products/black-2-slot-toaster.jpg');

    expect(appliance.instructionsLink).toEqual('images/appliance-instructions.png');
    expect(appliance.warrantyLink).toEqual('images/appliance-warranty.png');
  });

  it('gets the stars url', () => {
    expect(appliance.getStarsUrl()).toEqual('images/ratings/rating-50.png');
  });

  it('gets the price', () => {
    expect(appliance.getPrice()).toEqual('$18.99');
  });

  it('displays instructions and warranty in extraInfoHTML', () => {
    expect(appliance.extraInfoHTML()).toContain(
      `<a href="images/appliance-instructions.png" target="_blank">`
    );
    expect(appliance.extraInfoHTML()).toContain('Instructions');

    expect(appliance.extraInfoHTML()).toContain(
      `<a href="images/appliance-warranty.png" target="_blank">`
    );
    expect(appliance.extraInfoHTML()).toContain('Warranty');
  });
});
```
