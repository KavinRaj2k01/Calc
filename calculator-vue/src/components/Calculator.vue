<template>
    <div><div><h1> {{titles}}</h1></div>
    <div>
    <table border="2px">
        <tr> <td colspan="4" id="display"> {{number || '0'}} {{operator}} {{newNumber || ''}} {{res }}</td></tr>
        <tr>
            <td colspan="2" id="clrbtn" @click='clear'>CLR</td>
            <td colspan="2" id="delbtn" @click='deletefun'>DEL</td>
        </tr>
        <tr>
            <td @click='append("7")'>7</td>
            <td @click='append("8")'>8</td>
            <td @click='append("9")'>9</td>
            <td class="operator" @click='multi("X")'>X</td>
        </tr>
        <tr>
            <td @click='append("4")'>4</td>
            <td @click='append("5")'>5</td>
            <td @click='append("6")'>6</td>
            <td class="operator" @click='sub("-")'>-</td>
        </tr>
        <tr>
            <td @click='append("1")'>1</td>
            <td @click='append("2")'>2</td>
            <td @click='append("3")'>3</td>
            <td class="operator" @click='add("+")'>+</td>
        </tr>
        <tr>
            <td @click='append("3")'>0</td>
            <td @click='append(".")'>.</td>
            <td class="operator" @click='div("/")'>/</td>
            <td class="operator" @click='result'>=</td>
        </tr>

    </table>
    </div>
    </div>
</template>
<script>
export default {
name:'Calculator',
props:['titles','name'],
data(){
    return{
     number:'',
     newNumber:'',
     opClicked:'false',
     operator:'',
     res:''
    }
},
methods:{
    clear()
    {
        this.number=''
        this.newNumber=''
        this.opClicked='false'
        this.operator=''
        this.res=''
    },
    append(num)
    {
        if(this.opClicked==true)
        {
        this.newNumber=`${this.newNumber}${num}`;
        }
        else
        {
        this.number=`${this.number}${num}`;
        }
    },
    deletefun()
    {
        if(this.opClicked=='false')
        {
        this.number=this.number.slice(0,-1);
        }
        else
        {
        this.newNumber=this.newNumber.slice(0,-1); 
        }
    },
    multi(op)
    {
        this.operator=op;
        this.opClicked=true;
    },
    add(op)
    {
        this.operator=op;
        this.opClicked=true;
    },
    sub(op)
    {
        this.operator=op;
        this.opClicked=true;
    },
    div(op)
    {
        this.operator=op;
        this.opClicked=true;
    },
    result(){
        var a,b;
        if(this.operator=='X')
        {
            a=Number(this.number)
            b=Number(this.newNumber)
            this.res= " = " + (a * b) 
        }
        else if(this.operator=='/')
        {
            a=Number(this.number)
            b=Number(this.newNumber)
            this.res= " = " + (a / b) 
        }
        else if(this.operator=='+')
        {
            a=Number(this.number)
            b=Number(this.newNumber)
            this.res= " = " + (a + b) 
        }
        else if(this.operator=="-")
        {
            a=Number(this.number)
            b=Number(this.newNumber)
            this.res= " = " + (a - b) 
        }
    }
}
}
</script>
<style scoped>
.operator
{
    background-color:aqua;
}
table{
    width:400px;
    height:400px;
    text-align: center;
    margin: auto;
}
#display
{
    background-color: bisque;
    font-size: 150%;
}
#delbtn{
    background-color: red;
}
#delbtn:hover
{
    background-color: black;
    color:white;
}
#clrbtn
{
    background-color: salmon;
}
#clrbtn:hover{
    background-color:springgreen;
}
td{
    background-color:silver;
    border-radius: 5px;
    font-weight: bold;
}
td:hover{
  background-color: slateblue;
}
</style>