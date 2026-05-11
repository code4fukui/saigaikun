# saigaikun

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A simple, web-based framework for creating interactive, text-based disaster preparedness games. This project, created by [Code for FUKUI](https://github.com/code4fukui), provides multiple scenarios to teach emergency response strategies through a simple, choice-driven narrative.

## Demo

[**Play Saigaikun Live**](https://code4fukui.github.io/saigaikun/)


![Saigaikun main menu, asking "What will you fight?" with options for various disaster scenarios.](https://user-images.githubusercontent.com/1715217/156316472-5b6ed81d-18c4-4674-ac59-0e48cc2624ac.png)


## Features

-   **Interactive Scenarios**: Face various disasters like earthquakes, fires, and typhoons, making choices that lead to different outcomes.
-   **Educational Content**: Learn practical survival tips, such as hiding under a desk during a school earthquake or using a helmet in a typhoon.
-   **Simple Game Engine**: Built on `egadv.js`, a lightweight module for creating text-based adventures with minimal code.
-   **Easily Extensible**: Create and add new disaster scenarios by writing simple HTML and JavaScript files.

## How to Create Your Own Scenario

You can create your own scenarios using the [ES-Jam](https://code4fukui.github.io/htmlprac/) online editor.

1.  **Basic Setup**: Display a background and a line of text.
    ```html
    <script type="module">
    import { bg, show } from "https://js.sabae.cc/egadv.js";

    await bg();
    await show("A strong earthquake is coming!");
    await show("Make the right choices to survive.");
    </script>
    ```

2.  **Adding Choices**: Use an array of strings in the `show` function to present options to the player. The function returns the selected option.
    ```javascript
    const ans = await show("What do you do?", ["Fight", "Run", "Use Item"]);
    if (ans == "Fight") {
        await show("You fought.");
    } else if (ans == "Run") {
        await show("You ran away.");
    } else if (ans == "Use Item") {
        await show("You used an item.");
    }
    ```

3.  **Creating a Loop**: Use a `for` or `while` loop to repeat a section until a condition is met.
    ```javascript
    for (;;) {
        const ans = await show("What do you do?", ["Continue", "End"]);
        if (ans == "End") {
            break;
        }
    }
    await show("Loop ended.");
    ```

4.  **Linking to Another Page**: Redirect to another scenario or back to the main menu.
    ```javascript
    // Redirects to the main menu
    document.location = "./";
    ```

## Scenarios Included

-   **Earthquake**: A monster "Earthquake" has appeared. How do you escape?
-   **Fire**: A fire has broken out. Do you fight it, run, or use your phone?
-   **Cooking Fire**: A fire starts while you're cooking. Quick, what's the best way to put it out?
-   **School Earthquake**: An earthquake hits while you're in class.
-   **Typhoon**: A typhoon is approaching. Is it safe to go outside?
-   **Super Typhoon**: A massive typhoon has arrived. Where do you go for safety?

## Further Reading

This project was developed as part of a workshop with technical college students. You can read more about its creation (in Japanese) on the following blogs:

-   [Disaster Preparedness RPG 'Saigaikun' by Technical College Students and an Open Source Workshop](https://fukuno.jig.jp/3507)
-   [Learning Life Strategies from Technical College Seniors and an Introduction to Civic Tech with 'Saigaikun'](https://fukuno.jig.jp/3533)

## License

This project is available under the MIT License.