##常见垂直居中方式

1. **相对定位**
    
	    .content {
		  position: relative;
	      top: 50%;		//垂直居中
	      margin:0 auto;//水平居中
	      margin-top: -100px;//减去自身的高度一半

	      background-color: #6699FF;
	      width: 200px;
	      height: 200px;
	    }
2. **绝对定位**

	    .content {
		    width: 300px;
		    height: 300px;
		    background: orange;
		    
		    position: absolute;
		    left: 50%;
		    top: 50%;
		    transform: translate(-50%,-50%);//CSS3新特性 不需要知道自身宽高
		}
3. **Flex布局**

父容器：

    .wrapper{
    	justify-content: center;//项目在主轴上的对齐方式（X）
	    align-items: center;		//项目在交叉轴上如何对齐
	    display: -webkit-flex;
    }