# TempConversion
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';
import { log } from 'util';

class App extends Component {

	constructor(props) {
		super(props);
		this.state = {
			celcius: 0,
			fahren: 0
		}

	}


	componentDidMount() {
		this.setState({
			fahren: this.getFahrenheit(this.state.celcius)
		})
	}


	changeHandler = (e) => {
		switch (e.target.id) {
			case 'celcius':

				const celcius = e.target.value;

				this.setState({
					fahren: this.getFahrenheit(celcius),
					celcius: celcius
				})
				break;
			case 'fahren':
				const fahren = e.target.value;
				this.setState({
					celcius: this.getCelcius(fahren),
					fahren: fahren,
				})
				break;


			default:
				break;
		}
	}

	getFahrenheit(value) {
		return (value * 9 / 5) + 32;
	}

	getCelcius(value) {
		return (value - 32) * 5 / 9;
	}


	render() {
		const { celcius, fahren } = this.state
		return (
			<div className="containe" >
				<div className="forms">
					<img src="/122.png" className="image"  />
					<h1 className="text-center mt-2">Convert Temperature</h1>
					<h6 className="text-center">Superfast</h6>
					<div className="mt-2">
						<label htmlFor="celcius" className="label">Celcius</label>
						<div className="control">
							<input onChange={(e) => this.changeHandler(e)} value={celcius} className="input" placeholder="Celcius" type="number" id="celcius" />
						</div>
					</div>
					<div className="mt-2">
						<label htmlFor="celcius" className="label">Fahrenheit</label>
						<div className="control">
							<input onChange={(e) => this.changeHandler(e)} className="input" value={fahren} type="number" id="fahren" />
						</div>
					</div>
				</div>
			</div>
		);

	}
}


export default App;











.forms{
  height: 450px;
  width: 400px;
  margin: auto auto;
  background: #fff;
  box-shadow: #fcfcfc;
  padding: 30px;
}
.containe{
  background: #ebebeb;
  height: 100vh;
}
.mt-2{
  margin-top: 20px;
}
.image{
  margin: auto auto;
}
.text-center{
  text-align: center;
}
