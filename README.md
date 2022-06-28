# Quality

## Code can be self-documenting.

Here, I have authored a very captivating and touching story about the love one user has for an unfamiliar animal, and the unsuspected disdain the animal exhibits for the user.

```jsx
const didUserSpotAnimal = true;
const isAnimalFurry = true;
const doesAnimalRoar = false;
const shouldUserPetAnimal = isAnimalFurry && !doesAnimalRoar;
const didAnimalBiteUser = true;
const willAnimalFeelGuilt = false;
const canUserForgiveAnimal = true;
const wouldAnimalMakeGoodPet = !didAnimalBiteUser;
const isTheEnd = true;
```

_In case you didn’t notice, I wrote this entire tale using only booleans._

\***\*In Ancient Aliens Narrator voice\*\*** Is it apparent that these values are booleans because of the values they are assigned, or could there be another indicator?

**_Some ancient English theorists say yes._** The strategy used to name these values shouts “true or false” from the rooftops.

```jsx
**did**UserSpotAnimal, **is**AnimalFurry, **does**AnimalRoar, **should**UserPetAnimal,
**did**AnimalBiteUser, **will**AnimalFeelGuilt, **can**UserForgiveAnimal,
**would**AnimalMakeGoodPet, **is**TheEnd
```

<aside>
💡 Take note; you could also navigate and understand the flow logic in the story above even if the values are not there. It is interpetable. Readable: intuitive.

</aside>

Let’s take a look at how this story could have been written.

```jsx
const spottedAnimal = true;
const furry = true;
const roar = false;
const petAnim = furry && !roar;
const bitten = true;
const feelGuilt = false;
const forgiveAnim = true;
const makePet = !bitten;
const done = true;
```

<details>
  <summary>
    NOTE: Keystrokes / LOC are friend, not food.
  </summary>
Be not dazzled with all the saved keystrokes, because keystrokes are hardly the enemy. We perform more keystrokes in daily communication and planning than we actually do in the code editor every day.  
<br/><br/>
*(If anything, the uncontested 80 character limit per line of code enforced by Prettier by default is the enemy. 😒)*
<br/><br/>
The less keystrokes we make, the more obscure our code becomes. Same with lines-of-code. Our ability to write brief code is the antagonist to our ability to write easy-to-interpret, descriptive, self-documenting, maintainable code.

With good naming and descriptive code, we should never need this:

```jsx
// Clones the candidate object
const newObject = { ...oldObject }
```
</details>

Cool, it looks clean, brief, bad ass. But if we were to get rid of the assigned values and determine what all of these references actually referred to, we’d be up a creek without a paddle.

- “spottedAnimal” reads as though it will refer to an object describing an animal… that is spotted.
- “furry” hell if I know. Maybe a boolean, sure.
- “roar” alright, this is a verb — must be a function.
- “petAnim” verb, function, right? Also, idk who tf Anim is, but you should ask him/her first before invoking this function.
- “bitten” idk. could read as a boolean, sure.
- “feelGuilt” verb, reads as function.
- “forgiveAnim” verb, function.
- “makePet” verb, function.
- “done” maybe boolean, but “done” is often used as a callback identifier, so 🤷‍♀️.

## Name it what it is

> The act of naming things
> proves difficult for humans
> who have to think about it.

- _Matsuo Basho, Poet_
  >

Naming things doesn’t have to be hard. I dare say, most of the time we add difficulty to naming things simply because we’re trying to save keystrokes. We’re looking for what we can abbreviate, what words we can omit, etc.

<aside>
💡 **I can’t say this enough:** Keystrokes and lines of code are not the enemy. The more descriptive you can name things, and the extra lines of code it takes to format things in a clean manner, the more easily maintainable the code will be. 100% of the time.

</aside>

> **Arrays should be named with the plural word for whatever is inside.**

Arrays don’t have to include the word “list”, or “array” or anything like that. You can indicate that it is an array simply by indicating that it is plural. (With an “s”.)

```jsx
const users = [user0, user1, user2];
const results = [result0, result1, result2];
```

> **Boolean identifiers should ask a true or false question.**

```jsx
const didUserSpotAnimal = true;
const isAnimalFurry = true;
const doesAnimalRoar = false;
const shouldUserPetAnimal = isAnimalFurry && !doesAnimalRoar;
const didAnimalBiteUser = true;
const willAnimalFeelGuilt = false;
const canUserForgiveAnimal = true;
const wouldAnimalMakeGoodPet = !didAnimalBiteUser;
const isTheEnd = true;
```

> **Objects should be named as exactly what they describe.**

```jsx
const candidate = { firstName: "old", lastName: "greg", ...etc };
const branch = { id: 12345678, location: "wherever", ...etc };
const application = { ...whatever };
```

Object names should never be plural unless the object is being used as a map, in which case it should be descriptive to indicate so.

Using the modifier “map” is not discouraged, as it is a necessary clarification, whereas “list” is not.

```jsx
const questionsAndAnswers = {
  "are you ok?": "yeah i guess",
  "oh really?": "yep",
};

const stateAbbreviationsMap = {
  Texas: "TX",
  California: "Cali",
};

// "stateAbbreviations" would imply that it is a list
// of state abbreviations, as seen below. Thus; the
// "map" modifier shines.

const stateAbbreviations = ["TX", "CA", "NY", "YOLO"];
```

> **Numbers and Strings should be called exactly what they are.**

```jsx
const firstName = "Greg";
const city = "Townsville";
const age = 97;
```

In the case of a number that is referencing something specific, such as the number of times something has happened or the number of things that exist, do not be afraid to use a modifier to make it apparent.

```jsx
const renderCount = 12;
const numberOfDogs = 33;
```

Same thing applies if your number references the length of something.

```jsx
const applicationCount = applications.length;
const numberOfWords = "sup dude".split(" ").length;
```

> **Functions should be named like a verb phrase.**

```jsx
const getFooFromBar = (bar) => { /* ... */ }
const combineSomething = (some, thing) => { /* ... */ }
const determineSomething = (..args) => { /* ... */ }
const verbIt = (it) => { /* ... */ }

// Perform a check (verb) that results in a boolean.
const checkIsInputValid = (bar) => { /* ... */ }

```

---

## Writing good code.

Explicit is better than implicit.

```jsx
const example0 = a => !!verify(a) && c === a.substring(2, 9)

// Lord, these functions are difficult to visually parse.
// But, beyond that, they're just... nasty.

// Sure, you authored this code so it makes sense to you...
// But it doesn't hurt to put in the extra effort so that
// the next person developing this code actually has
// a clue what is going on lol.

const example1 = (string) => {
  const condition0 = = !!verify(string)
  const substring = string.substring(2, 9)
  const condition1 = valueToMatch === substring
  return condition0 && condition1
}
```

Legos are better than.. not Legos

```jsx
const example2 = () => {
  // logic
  // logic
  // logic
  // logic
  // logic
  // logic
  // logic
  // logic
  // logic
};

// Great, so example2 is complex so naturally its like
// 150 lines of code. Shit happens, right?

// But what if it could be... less?
// What if it could be concerned with the overall
// outcome based on the results of more modular
// computations?

// The broken down functions below can all be tested,
// will be easier to interpret piece by piece, and not
// overwhelm the developer's sensse of contextul memory.
// And, let's not forget: they become reusable.

const example3 = () => {
  // logic
  // logic
  // logic
  something = example3Logic0();
  somethingElse = example3Logic1();
  // Here, as long as you have an idea
  // what data came out of those^ 2 functions,
  // you can release their contained logic
  // from your memory. When their logic was
  // all inlined, you needed to maintain everything
  // to have this code running in your head.
  example3Logic2();
};

const example3Logic0 = () => {
  // logic
  // logic
};

const example3Logic0 = () => {
  // logic
  // logic
};

const example3Logic0 = () => {
  // logic
  // logic
};
```

Consistency is key.

```jsx
const add10 = (number) => {
  return number + 10;
};

// The above function will always be better than...

const add10 = (number) => number + 10;

// ... because we don't actually have such silly functions
// running around in our codebases. This is arbitrary,
// but in real life, functions grow, they become more
// capable.

// Just make it easy to maintain, as well as interpret,
// by just being explicit about the return and opting
// for arrow parenthesis 100% of the time.

// Consistency makes for maintainability. This even applies
// to something as small as a paren here and thur.
```

Data driven development.

```jsx
// It is no secret that we can not trust our services. 😄

// But once we have received whatever it is they send us,
// we should be able to trust that we have **something** that we
// are providing on to the rest of our logic -- and we **know
// what it is.**

// We **do nottttt** want data running around that we are
// unfamiliar with...

// We do nottttt need?.this?.everywhere because we should
// determine at the beginning if a piece of data exists, and
// if not, provide a default that will not break our logic.
// At least when nullish defaulting we can trust the data
// as it marches forth. :)
```
