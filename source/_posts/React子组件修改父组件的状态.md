---
title: 'React子组件修改父组件的状态'
tags: []
date: 2016-10-18 12:46:35
---

在React中，父子组件间的通信是通过props来传递参数的。一般情况下，父组件传一个值给子组件，同时还要传一个修改该值的方法函数。这样，在子组件中调用这个方法函数才能修改该值，并再次传给子组件，从而修改子组件状态。
虽然这个数据流非常绕，至少是能接受的，但一旦要传非常多的参数给子组件的时候，这样就很麻烦，比如要传十个参数，就必须再传十个修改函数，而且这十个修改函数还必须在父组件中写一遍定义，结果就如下一般繁琐：
```js
class App extends Component {
    constructor(props) {
        super(props);
        
        this.state = {
            step: 1,
            isHome: '',
            isNewCar: false,
            plateNo: '',
            name: '',
            idCard: '',
            brandModel: '',
            engineNo: '',
            vin: '',
            hasRecord: 0,
            registerDate: ''
        };
    };

    //修改参数的函数
    setStep() {
        this.setState({
                step: ++this.state.step
            });
    }
    
    //修改参数的函数
    setIsHome(val) {
        this.setState({
                isHome: val
            });
    }

.
.
.
.
.
.


    //修改参数的函数
    setRegisterDate(val) {
        this.setState({
                registerDate: val
            });
    }

    render() {
        return (
            <div>
                <IndexDesk 
                    step={this.state.step} 
                    isHome={this.state.isHome} 
                    isNewCar= {this.state.isNewCar}
                    plateNo={this.state.plateNo} 
                    idCard={this.state.idCard}
                    brandModel={this.state.brandModel}
                    engineNo={this.state.engineNo}
                    vin={this.state.vin}
                    hasRecord={this.state.hasRecord}
                    registerDate={this.state.registerDate}

                    setStep={this.setStep.bind(this)}
                    setIsHome={this.setIsHome.bind(this)}
                    .
                    .
                    .
                    setRegisterDate={this.setRegisterDate.bind(this)}

                    />
            </div>

        );
    };
}
```
这是我最先想到的思路，显然，这个代码冗余实在是太大，后来发现，其实我可以传递一个函数就可以搞定所有的参数修改函数了：
```js
//修改根组件的状态
    setSet(obj) {
        this.setState(obj);
    }
```

之前的组件可以写成如下模样
```js
class App extends Component {
    constructor(props) {
        super(props);
        
        this.state = {
            step: 1,
            isHome: '',
            isNewCar: false,
            plateNo: '',
            name: '',
            idCard: '',
            brandModel: '',
            engineNo: '',
            vin: '',
            hasRecord: 0,
            registerDate: ''
        };
    };
    
//修改根组件的状态
    setSet(obj) {
        this.setState(obj);
    }
    

    render() {
        return (
            <div>
                <IndexDesk 
                    step={this.state.step} 
                    isHome={this.state.isHome} 
                    isNewCar= {this.state.isNewCar}
                    plateNo={this.state.plateNo} 
                    idCard={this.state.idCard}
                    brandModel={this.state.brandModel}
                    engineNo={this.state.engineNo}
                    vin={this.state.vin}
                    hasRecord={this.state.hasRecord}
                    registerDate={this.state.registerDate}

                    setSet={this.setSst.bind(this)}
                    />
            </div>

        );
    };
}
```

代码瞬间少了很多，世界顿时美好了起来