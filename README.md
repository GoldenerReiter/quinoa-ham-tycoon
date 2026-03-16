Viva Quinoa Naturals | Tycoon Simulator

"Discover the perfect balance between quality, affordability, and absurd profitability."

Welcome to the ultimate Greenwashing and corporate crisis management simulator. Viva Quinoa Naturals is a web-based incremental (tycoon/idle) game where you run a promising superfood startup.

Your goal is to maximize profits by mixing organic quinoa with cheap pork scraps, all while maintaining a facade of being an ethical, sustainable, and 100% plant-based brand.

Objective

You must manage your Seed Capital and your Trust Score (Reputation).

If you manufacture pure products (100% quinoa), your Trust Score will increase, but you will lose money due to high certification costs.

If you pad your products with cheap ham (or worse), your profit margins will explode, but consumers will notice, and your Trust Score will plummet.

Game Over conditions:

Your Trust Score reaches 0% (the public uncovers your fraud).

Your Capital falls below zero, and the grace period expires (Bankruptcy due to health fines or debt).

Core Mechanics

Supply Market: Purchase Ancestral Biomass (Quinoa) and Meat Alternative (Ham) based on dynamic market prices.

Production Labs (Kitchens): Configure the exact recipe for your products. Ranging from "Light Smoothies" (pure loss, high reputation) to "Keto Bites" (pure ham, fast cash). You can purchase multiple branches to run different production lines simultaneously.

Autonomous Cooperative (Bots): Automate your empire by hiring Purchasing Assistants, Mixers, and Brand Ambassadors so the game plays itself.

R&D (Tech Tree): Invest in bribes, political lobbying, lawyers, and deceptive packaging to evade fines and increase your base prices.

Dynamic Events: Survive "Andean Droughts" (quinoa price x3), capitalize on "Vegan Booms", or mitigate "Viral Scandals" on social media.

Deep Web Market: Unlock experimental, highly radioactive ingredients that yield massive production output but destroy your reputation almost instantly.

Technical Implementation

The game is built as a monolithic, client-side Single-File Application. It requires no external assets, build steps, or backend servers.

Architecture & Patterns

The JavaScript logic is structured using a Module Pattern within a global Game namespace to prevent global scope pollution and organize features logically.

Game.state: A centralized, deeply serializable object containing the entire mutable state of the game (inventory, money, reputation, active events, bot counts, unlocked tech).

Game.cfg: Static configuration data containing base prices, technology tree definitions, and event parameters.

Game Loop (Game.Core.loop): A central setInterval loop running at 1 tick per second (1000ms). It acts as the heartbeat of the game, sequentially triggering bot actions (Game.Bots.tick), decrementing event timers (Game.Events.tick), and evaluating win/loss conditions (Game.Core.checkGameOver).

UI Rendering and State Reactivity

The application relies on Vanilla JavaScript DOM manipulation (document.getElementById, innerHTML).

A master Game.UI.update() function acts as a reactive render cycle. It calculates derived state (e.g., adjusting selling prices based on current reputation or applying event multipliers) and updates the DOM accordingly.

Complex components, like the multiple Production Labs (Game.Kitchens.renderAll), dynamically generate HTML strings and inject them into the DOM, attaching inline event listeners that map back to the Game object.

Persistence

Game progress is preserved across sessions using the browser's localStorage.

Deep Merging: Upon initialization, the load sequence parses the saved JSON string and performs a deep merge with the default Game.state. This ensures that if the game code is updated with new features or state variables, older save files won't cause undefined reference errors.

Silent Autosave: A background interval automatically serializes and commits the state to localStorage every 10 seconds.

Technology Stack

HTML5: Semantic structure and layout within a single index.html file.

JavaScript (ES6): Vanilla JS handling the game loop, state management, and DOM manipulation without the overhead of heavy frameworks like React or Vue.

Tailwind CSS: Imported via CDN for rapid, utility-first styling. It handles the "glassmorphism" effects, modern typography, and responsive grid layouts that mimic a sleek Silicon Valley startup aesthetic.

Corporate Legal Disclaimer: Any resemblance to real food industry companies, greenwashing practices, or pyramid schemes is purely coincidental. Viva Quinoa Naturals is an interactive parody.