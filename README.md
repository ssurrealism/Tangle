<img title="" src="docs/logo.svg" alt="s" width="838">

> **Note**
> This project is not ready for general use:
> 
> - `terminal app` is unfinished
> - `data server` is unfinished
> - `web app` is unfinished
> - no `Tangle Cloud` yet
> - no `web browser extension` yet

---

#### Simple yet smart lists of whatever you want

You, the user, defines what kinds of items there are.

Common item types are pre-defined, optional, alterable and restorable so you don't have to do anything. 

E.g. you can define such items to use in your lists :

* **`βοΈ email`**  --  *(btw. Tangle can sync with your email or just replace if, if you want)*
* **`π contact`**
* **`π πΌοΈ βοΈ file`**  --  *(btw. Tangle can sync with your local storage as well as cloud, if you want)*
* **`β task`**
* **`π routine`**
* **`βοΈ note`**
* **`π goal`**
* **`π€ π account`**  --  *(btw. Tangle browser plugin can handle your online accounts, if you want)*
* **`π§³ equipment`**
* **`π² transaction`**
* **`π¦ loan`**
* **`πΊοΈ place`**
* **`π journal`**
* `π’ some arbitrary metric`  --  *(e.g. smart home combined state or single measurement)*
* ...

#### About those lists

* List can contain items of only one kind or many - you decide.
* There is a handy filter and global view where you get a list per each item type, with all items of that type.
* Every item can point to and contain items of any other item type.
* Every item type is definable and editable: its emoji (optional), its name, what fields does it have etc.
* Every item can have required and optional fields, with content (full or some part) encrypted & protected if needed.
* What kind of content is allowed where (date, check, text, number etc.) is also definable.
* Items and lists can be self updating, sync with external programs and be used interchangeably with those programs.
* Instead of syncing with external programs and services you can sync with [Tangle Cloud](https://cyber.harvard.edu/projectvrm/Privacy_Manifesto) to be sure your data is yours and only yours.

#### Example use cases

* User can define **`π§³ equipment`** and **`π file`**, then scan or take a pic of any equipment related documents such as purchase receipts, warranties, instructions and repair reports. Those files can be linked as children of a given equipment.
* **`π Document`** such as signed `Terms and Conditions` or `Privacy Policy` can be stored under **`π€ π account`** items to not lose it and for easy access.

## How to run it and see project board/roadmap

Instead of using GitHub Issues, GitHub Projects, JIRA or something else Tangle tasks, docs and everything else is managed by Tangle itself. If you want to see what is going on right now in this project or how it already looks like in action, run below. 

```shell
# download Tangle and python requirements for cli and server
git clone https://github.com/ssurrealism/Tangle
cd Tangle
python -m venv .venv
source .venv/bin/activate
pip -r requirements.txt

# run cli (no server needed)
python tangle.py
python tangle.py read note
python tangle.py read task
python tangle.py create task label 'feat' due_date '2023-03-13' project 'cli' title 'implement help command'

# Tangle uses json and yaml files as database right now so you can also read those manually if you want
cat docs/_data/_config/task.yaml
cat docs/_data/task.json

# run server
python tangle.py server

# run webapp (keep server running and run below commands in new terminal)
cd Tangle/app/
npm install
npm run dev
# now visit localhost:5173 in your web browser
```

## Technical details

#### Parts of tangle ecosystem

* **Data directory**
  
  Directory on your computer or phone or any other device where all lists and items are stored.

* **Data server**
  
  Program that exposes data stored inside **Data directory** to the internet. Used by **PWA** and **Terminal app**.

* **Website and mobile app (PWA)**
  
  Self explanatory. Can work on any data exposed by **Data server**. Has build in support for **Tangle Cloud**.

* **Tangle Cloud**
  
  For people that just want to use **PWA** working out of the box with data synced and accessible across all of their devices. It's an instance of **Data server** managed by tangle authors. **Data directory** for each user in Tangle Cloud is fully encrypted so that nobody who has access to Tangle Cloud can access user data.

* **Terminal app**
  
  Command line app, can work on any data exposed by **Data server** or directly on **Data directory** if computer has access to it.

* **Library**
  
  Python package, used by both **Terminal app** and **Data server** to create, read, update and delete data in **Data directory**.
  Can be used to write scripts and other tools. Library also implements all build-in integrations and analytics.

#### Integrations & Analytics

* **Topics**: **`Google Workspace`**, **`Banking`**, **`Crypto`**, **`eCommerce`**, **`items market`**, **`sharing and renting`**, **`Arbitrary internet service`**, ...
* **Examples**: `gmail`, `google drive`, `google contacts`, `mBank`, `Binance`, `Amazon`, `Revolut`,  `PKO`, `ING`, `BPC`, `Coinbase`, `DEGIRO`, `Exante`, `TradingView`, ...
* **Functions**: accounts automatic detection and easy+delegated management (e.g. closing, raport of what is unused (not necessary) or duplicates features),..., `progress and stagnation detection`, `financial analytics`, `projects analytics`

# 
