<div>
	<div>
		<img src=https://raw.githubusercontent.com/Byron2016/00_forImages/main/images/Logo_01_00.png align=left alt=MyLogo width=200>
	</div>
	&nbsp;
	<div>
		<h1>068_00_React_SASS_Avatar</h1>
	</div>
</div>

&nbsp;

## Project Description

This tutorial is a practice/**COPY** of **ReactJS con SASS: Programando la web de Avatar**. following Eduardo Fierro's tutorial.</br> 
&nbsp;</br>
    - [ReactJS con SASS: Programando la web de Avatar](https://www.youtube.com/watch?v=NXNGW6AAyP4).</br>
	[![Youtube](https://img.shields.io/static/v1?label=&message=ver%20en%20youtube&color=FF0000&logo=youtube&logoColor=white&style=for-the-badge)](https://www.youtube.com/watch?v=NXNGW6AAyP4)</br>
	
&nbsp;

## Technologies used

![ViteJS](https://img.shields.io/static/v1?label=&message=ViteJS&color=purple&logo=vite&logoColor=white&style=for-the-badge)
![SASS](https://img.shields.io/static/v1?label=&message=SASS&color=CC6699&logo=sass&logoColor=white&style=for-the-badge)
![SUIT Methodology](https://img.shields.io/static/v1?label=&message=suitcss&color=lightblue&logo=suit&logoColor=white&style=for-the-badge)
![ReactJS](https://img.shields.io/static/v1?label=&message=reactjs&color=17A1E6&logo=react&logoColor=white&style=for-the-badge)

## Steps

### Table of Contents
1. Create a new project
2. SASS installation
3. Official web analysis
4. Create Header context

### Create a new project
We are going to use **Vite** like a build tool, using **Reactjs**; then it is necesary to excecute these commands

```bash
	npm create vite@latest
	cd avatar-the-way-of-water
	npm i
	npm run dev
```

### SASS installation
We are going to use **Vite** like a build tool, using **Reactjs**; then it is necesary to excecute these commands

```bash
	npm i sass -D
```

### Official web analysis
It is necessary to use [Figma](https://www.figma.com/) with the finality to make a desing analisys.
- New design file
- Resources - Plugings
- html.to.design
- Paste web page address


### Create Header context
- Prepare original files
	- Change App.css to App.scss and delete its content
	- Change index.css to index.scss and delete its content
	- Into main.jsx change import from index.css to index.scss
	- Into App.jsx 

		```javascript
		import './App.scss'

		const App = () => {
		return (
			<div className="App">
				Avatar
			</div>
		)
		}

		export default App
		```

- Add Reset.css
	- Ir a [Reset-CSS](https://github.com/eduardofierropro/Reset-CSS) 
	- Create a file /src/reset.scss
	- Import /src/reset.scss into /src/main.jsx

		```javascript
		....
		import './reset.scss'
		....
		```
- Add Context
	- Create file /src/provider/Provider.jsx
	- Instalar uuid
		```bash
		npm i sass -D
		```
	- Disable avatar.com css and copy everything equivalent to the menu.
	- Add into /src/provider/Provider.jsx
	```javascript
	import { v4 as uuidv4 } from "uuid"
	import { createContext } from "react"

	const bbdd = {
		header: {
			menu: [
				{id: uuidv4() , title : "Home"        , href :"#"},
				{id: uuidv4() , title : "Movies"      , href :"#"},
				{id: uuidv4() , title : "Games"       , href :"#"},
				{id: uuidv4() , title : "Experiences ", href :"#"},
				{id: uuidv4() , title : "Experiences" , href :"#"},
				{id: uuidv4() , title : "Community"   , href :"#"},
				{id: uuidv4() , title : "Publishing"  , href :"#"},
				{id: uuidv4() , title : "Partnerships", href :"#"},
				{id: uuidv4() , title : "Our Team"    , href:"#"}
			],
			rrss : [
				{ id : uuidv4() , title : 'Facebook'  , href : '#' , icono : 'facebook'},
				{ id : uuidv4() , title : 'Twitter'   , href : '#' , icono : 'twitter'},
				{ id : uuidv4() , title : 'Instagram' , href : '#' , icono : 'instagram'},
				{ id : uuidv4() , title : 'Youtube'   , href : '#' , icono : 'youtube'},
			]
		},
		hero : {
			h2 : 'Avatar the way of water',
			claim : 'Watch the brand-new trailer and experience Avatar: The Way of Water in 3D on December 16.'
			,
			buttons : [
				{ id : uuidv4() , title : 'Get tickets'   , href : '#'},
				{ id : uuidv4() , title : 'Watch Trailer' , href : '#'},
			]
		}
	}
	```

	- Header
		- Create file /src/components/Header/Header.jsx
		- Create file /src/components/Header/Header.scss
		- into file /src/components/Header/Header.jsx
			- Add Header 
			```javascript
			import { useContext } from 'react'
			import { GlobalContext } from './../../provider/Provider'
			import './Header.scss'

			export const Header = () => {
				return(
					<header className="Header">
						<div className='Wrapper'>
							<Logo />
							<Hamburger />
							<Nav />
							<Rrss />
						</div>
					</header>
				)
			}

			const Logo = () => {
				return(
					<h1 className='Header'>
						<a href='#' title='Avatar' className='Header-logo'>
							<img src='#' alt='Avatar' className='Header-img'/>
						</a>
					</h1>
				)
			}
			....
			```
			- Add Nav 
			```javascript
			....

			const Nav = () => {

				const { header } = useContext(GlobalContext)
				const { menu } = header

				return(
					<nav className='Header-nav'>
						<ul className='Header-ul'>
							{ menu.map( ( { id, title, href })=> 
								<li 
									key={ id } 
									className={`Header-li ${ title === "Home" ? "isActive" : "" }`}> 
									<a className='Header-a' href={ href } title={ title }>
										{ title }
									</a>
							</li>
							)}
						</ul>
					</nav>
				)
			}
			....
			```
			- Add Rrss 
			```javascript
			....

			const Rrss = () => {
				const { header } = useContext(GlobalContext)
				const { rrss } = header

				return(
					<ul className='Header-rrss'>
						{rrss.map(({ id, title, href, icono}) => 
							<li key={ id }  className='Header-li'>
							<a className='Header-rs' href={ href } title={ title }>
								<Icono nombre={ icono }/>
							</a>
						</li>
						)}
					</ul>
				)
			}
			....
			```
			- Add Hamburger: Download hamburger.svg and save it into public/assets/icons/hamburger.svg
			```javascript
			....

			const Hamburger = () => {
				return(
					<button className='Header-btn'>
						<img className='Header-svg' src='assets/icons/hamburger.svg' alt='menu'/>
					</button>
				)
			}
			....
			```
			- Add Icono: It is necesary to erase bootstrap classes and if exist class fill-ru it is necessary to delete it.
			```javascript
			....
			const Icono = ({ nombre }) => {
				return(
					<>
						{ nombre === 'facebook'  && <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16"><path d="M16 8.049c0-4.446-3.582-8.05-8-8.05C3.58 0-.002 3.603-.002 8.05c0 4.017 2.926 7.347 6.75 7.951v-5.625h-2.03V8.05H6.75V6.275c0-2.017 1.195-3.131 3.022-3.131.876 0 1.791.157 1.791.157v1.98h-1.009c-.993 0-1.303.621-1.303 1.258v1.51h2.218l-.354 2.326H9.25V16c3.824-.604 6.75-3.934 6.75-7.951z"/></svg> }
						{ nombre === 'twitter'   && add svg icon from bootstrap icons }
						{ nombre === 'instagram' && add svg icon from bootstrap icons }
						{ nombre === 'youtube'   && add svg icon from bootstrap icons }
					</>
				)
			}
			```
		- Add Header component into file /src/App.jsx
		```javascript
		import './App.scss'
		import { Header } from './components/Header/Header.jsx'

		const App = () => {
		return (
			<div className="App">
				<Header />
			</div>
		)
		}

		export default App
		```

