---
title: 'React中事件传参的写法'
tags: []
date: 2016-10-21 11:09:49
---

最近在尝试React，发现之前很多用jQuery就能轻松解决的事情，现在遇到了新的挑战。当然这并不表示React不行，而是我还需要更多的研究和探索。React中的点击事件，想要传参数给方法，始终不得要领，现在摸索出一套写法，也许不是很完善，但先记录下来，以备以后改进

    <span class="hljs-keyword">class</span> SchemeSwitcher extends Component {
        constructor(props){
            super(props);

            <span class="hljs-keyword">this</span>.handleClick = <span class="hljs-keyword">this</span>.handleClick.bind(<span class="hljs-keyword">this</span>);

        };

        handleClick(event) {
            console.log(event.target.dataset.index);
        }

        render() {

            <span class="hljs-keyword">const</span> listShows = appInfo.threeSchemeNameList.map((nameStr, index) =&gt; {
                <span class="hljs-keyword">let</span> classStr = (index === <span class="hljs-keyword">this</span>.props.schemeIndex) ? <span class="hljs-string">'selected'</span> : <span class="hljs-string">''</span>;

                <span class="hljs-keyword">return</span> (
                    <span class="xml"><span class="hljs-tag">&lt;<span class="hljs-title">li</span> <span class="hljs-attribute">className</span>=<span class="hljs-value">{classStr}</span> <span class="hljs-attribute">key</span>=<span class="hljs-value">{index}</span> <span class="hljs-attribute">data-index</span>=<span class="hljs-value">{index}</span> <span class="hljs-attribute">onClick</span>=<span class="hljs-value">{this.handleClick}</span>&gt;</span>{nameStr}<span class="hljs-tag">&lt;/<span class="hljs-title">li</span>&gt;</span>
                )

            });

            return (
                <span class="hljs-tag">&lt;<span class="hljs-title">ul</span> <span class="hljs-attribute">className</span>=<span class="hljs-value">"switcher"</span>&gt;</span>
                    {listShows}
                <span class="hljs-tag">&lt;/<span class="hljs-title">ul</span>&gt;</span>

            );
        };

    }</span>`</pre>

    其中：

    <pre class="prettyprint">`<span class="hljs-tag">&lt;<span class="hljs-title">li</span> <span class="hljs-attribute">className</span>=<span class="hljs-value">{classStr}</span> <span class="hljs-attribute">key</span>=<span class="hljs-value">{index}</span> <span class="hljs-attribute">data-index</span>=<span class="hljs-value">{index}</span> <span class="hljs-attribute">onClick</span>=<span class="hljs-value">{this.handleClick}</span>&gt;</span>{nameStr}<span class="hljs-tag">&lt;/<span class="hljs-title">li</span>&gt;</span>

虽然key是React必须传的，但在组件中却不能获取； 

想通过onClick={this.handleClick(index)}这样的方式来直接传参数，但试过了，不行，函数在渲染时就被执行了； 

最后想到了用data-，可以了，不过写法跟$(this).data(‘index’)不一样哦。其实页可以用jQuery，但既然是想尝试新的东西，还是扬弃过去，使用js的原生写法吧：event.target.dataset.index。