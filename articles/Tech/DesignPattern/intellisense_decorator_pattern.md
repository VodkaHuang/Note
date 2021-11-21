```javascript
window.onload = function() {
    let cc = new ConcreteComponent();
    let d_a = new ConcreteDecoratorA();
    let d_b = new ConcreteDecoratorB();

    d_a.SetComponent(cc);
    d_b.SetComponent(d_a);
    d_b.Operation();
}

/**抽象Component類別 */
class Component {
    Operation() {}
}

/**Component的具體物件 */
class ConcreteComponent extends Component {
    Operation() {
        console.log('這裡執行具體物件要做的事');
    }
}

/**Decorator用來擴充Component的功能 */
class Decorator extends Component {
    constructor() {
        super();
        this.comp;
    }
    SetComponent(p_comp) {
        this.comp = p_comp;
    }
    Operation() {
        if (!this.comp) this.comp.Operation(); //實際執行的是ConcreteComponent的Operation()
    }
}

/**具體裝飾物件A */
class ConcreteDecoratorA extends Decorator {
    constructor() {
        super();
        this.addedState;
    }
    Operation() {
        this.comp.Operation();
        this.addedState = '裝飾物件A獨有的變數';
        console.log('裝飾物件A要做的事');
    }
}

/**具體裝飾物件B */
class ConcreteDecoratorB extends Decorator {
    constructor() {
        super();
    }
    Operation() {
        this.comp.Operation();
        this.AddedBehavior();
        console.log('裝飾物件B要做的事');
    }
    AddedBehavior() {
        console.log('裝飾物件B獨有的方法');
    }
}
```