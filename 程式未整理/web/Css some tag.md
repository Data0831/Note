# Css some tag

# fundamental
```css=
.font {
    font: 16px bold Arial, Helvetica, sans-serif;
    /* font short hands: size weight family*/
    font-size: 16px;
    font-weight: bold;
    /*填充程度*/
    line-height: 1.5em;
    text-decoration: underline;
    /* underscore */
    text-transform: uppercase;
    word-spacing: 1em;
    letter-spacing: 1em;
}

.margin .padding {
    width: 80%;
    height: 500px;
    margin: auto;
    /*can auto set the block to center*/
    padding: 20px;
    text-align: center;
    box-sizing: border-box;
    /* let border not adding to content width */
}

.border {
    border-top: 5px solid blue;
    border-right: 8px dotted dodgerblue;
    border-bottom: 1px double firebrick;
    border-left: 5px red solid;
    border-bottom-width: 8px;
    border-width: 5px;
    border-color: aliceblue;
    border-radius: 36px;
}

.background {
    background-color: #fff;
    background-image: url("#");
}

.list {
    list-style-image: url("#");
    list-style: square;
}

.clearfix {
    clear: both;
    /* let float clear */
}

.position {
    position: relative;
    /* absoulute/fixed */
    left: auto;
    top: auto;
    right: auto;
    bottom:auto;
    
}
```