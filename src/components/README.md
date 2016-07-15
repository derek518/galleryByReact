##react demo

������ݵĽṹ���Ϊ

```bash
let imageDatas = [{
  filename:'1.jpg',
  title:'Heaven of time',
  desc:'Here he comes Here comes Speed Racer.'
},{
  filename:'2.jpg',
  title:'Heaven of time',
  desc:'Here he comes Here comes Speed Racer.'
}];
```

�����ݽ��д���ʹ������ִ�е���������

```bash
imageDatas =(function(imageDatasArr) {
  for (var i = 0, j = imageDatasArr.length; i < j; i++) {
    var singleImageData = imageDatasArr[i];
    singleImageData.imageURL = require('../images/' + singleImageData.filename);
    imageDatasArr[i] = singleImageData;
  }
  return imageDatasArr;
})(imageDatas);
```

�����ӿ�

```bash
//��ܼ����
class AppComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state ={

    }
  }
  
  //������Ⱦ
  render() {
    return (
      <section className="stage" ref="stage">
        <section className="img-sec">

        </section>
        <section className="control_nav"></section>
      </section>
    );
  }
}

AppComponent.defaultProps = {
};

//�����ṩ�ӿ�
export default AppComponent;
```

ҳ��������Ⱦ

```bash
//ImgFigure���
let ImgFigure = React.createClass ({
  render() {
    return (
	  <figure className="img-figure">
        <div class="img-wrap">
          <img src={this.props.data.imageURL}/>
          <figcaption>
            <h2 className="img-title">{this.props.data.title}</h2>
            <div className="img-back">
              <p>{this.props.data.desc}</p>
            </div>
          </figcaption>
        </div>
      </figure>
	)
  }
})
class AppComponent extends React.Component {
  ...
  render() {
    let imgFigures = [];
	imageDatas.forEach(function (value, index) {
	  imgFigures.push(<ImgFigure key={index} data ={value} />);
	});
    return (
      <section className="stage" ref="stage">
        <section className="img-sec">
          {imgFigures}
        </section>
        <section className="control_nav"></section>
      </section>
    );
  }
}
```

����ҵ����ӵ���¼�

* ��һ����д
```bash
let ImgFigure = React.createClass ({
  handleClick(e) {
    alert(1);
    e.stopPropagation();
    e.preventDefault();
  },
  render() {
    <figure className="img-figure">
	  <div class="img-wrap" onClick={this.handleClick}>
	    <img src={this.props.data.imageURL}/>
	    <figcaption>
		  <h2 className="img-title">{this.props.data.title}</h2>
		  <div className="img-back" onClick={this.handleClick}>
		    <p>{this.props.data.desc}</p>
		  </div>
	    </figcaption>
	  </div>
    </figure>
  }
})
```
* �ڶ�����д
```bash
let ImgFigure = React.createClass ({
  handleClick(e) {
    this.props.inverse();
    e.stopPropagation();
    e.preventDefault();
  },
  ...
})

class AppComponent extends React.Component {
  ...
  inverse() {
    return function() {
		alert(1);
	}
  }
  
  render() {
    ...
	imageDatas.forEach(function (value, index) {
	  imgFigures.push(<ImgFigure key={index} data ={value} inverse={this.inverse()}/>);
	});
  }
}
```

�ο�����

* [ES5��ES6](http://www.cnblogs.com/Mrs-cc/p/4969755.html)������

* �ο�materliuԭͼƬ��תЧ��[demo](http://materliu.github.io/gallery-by-react/)

* ���ĵ�ַ[https://github.com/fugehappy/galleryByReact](https://github.com/fugehappy/galleryByReact)















