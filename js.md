
# 数字到字节 字节到数字

function createBuffer(v){
    var b = new ArrayBuffer(4),
        vw = new DataView(b);
    vw.setUint32(0,v,true);
    return b;
}

a = createBuffer(2)
let view = new DataView(a);
console.log(view.getUint32(0,true));
