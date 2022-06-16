
# When to use grid
- จัด Layout ที่ต้องคอนโทรล 2 มิติ
- จัด Layout ทั้ง page
- ใช้ทำ responsive ได้โดยไม่ต้องเขียน media query
- ทำ Photo gallery

# Cheat Sheet
https://css-tricks.com/snippets/css/complete-guide-grid/


# Properties for the Parent

`display:grid`  
`grid-template-rows`   
`grid-template-columns`  
`grid-template-areas`



### จัดการช่องว่าง
`grid-row-gap`  
`grid-column-gap`  
`grid-gap`

### จัดการ content,items
`justify-content` : จัดgrid-cell ทั้งหมดหรือ grid-track แนวนอน ภายใน grid-container (default: stretch 
`align-content` : จัดgrid-cell ทั้งหมดหรือ grid-track ดิ่ง ภายใน grid-container (default: stretch)  
`justify-items` : จัดสิ่งที่อยู่ใน grid-cell แนวนอน (default:stretch)  
`align-items` : จัดสิ่งที่อยู่ใน grid-cell แนวดิ่ง (default:stretch)

### จัดการ implicit cell

`grid-auto-flow` : จัดการกับ grid-cell ที่ล้นออกมา (implicit grid) (row,column,dense)
`grid-auto-rows` : กำหนดขนาดของ implicit grid
`grid-auto-columns` : กำหนดขนาดของ implicit grid



# Properties for the Children

### จัดตำแหน่ง grid-cell
`grid-column-start`  
`grid-column-end`  
`grid-column`  
  
`grid-row-start`  
`grid-row-end`  
`grid-row`

value : <grid-line-start> / <grid-line-end> or <span>

### จัด content ใน grid-cell
`justify-self`  
`align-self`

# Sizing keyword, Sizing Function 

`px,%,vh,vw,rem,em` : ใช้หน่วยพวกนี้ได้หมด  
`fr` : นำพื้นที่ว่างที่เหลือมาแบ่งเป็น fraction  
`min-content` : หากมีหลายคำจะ wrap โดยอิงจากคำที่ยาวที่สุด // ถ้ามีคำเดียวก็อาจจะ overflow ได้  
`max-content` : ไม่ wrap ปล่อยให้ overflow  
`auto` : เหมือน fr แต่สู้ fr ไม่ได้ถ้าเกิดใช้พร้อมกันแล้วต้องมีการแบ่งพื้นที่  
`minmax(<min_value>,<max_value>)`  กำหนดขนาดต่ำสุด,สูงสุดของ grid-cell;


# Repeat function with keyword

`repeat(8,1fr)` : กำหนดจำนวนที่ใช้ซ้ำและขนาด  
`auto-fill` : Fit as many possible columns as possible on a row, even if they are empty.  
`auto-fit` : Fit whatever columns there are into the space. Prefer expanding columns to fill space rather than empty columns.


# Practice

- กำหนดให้ grid ขึ้นแถวใหม่เมื่อขนาดเล็กกว่าที่กำหนด
```css
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
```

- กำหนดความสูงโดยอิงจาก width (เช่น gallery รูปภาพ)
```css
 grid-template-rows: repeat(7,5vw);
```

- ใน grid-template ใช้ fr กับบริเวณที่อยากให้ปรับขนาดตาม responsive 
- กำหนด grid name กับ layout ใหญ่ๆจะสะดวกกว่าเวลาที่ต้องทำ media-query (ไม่ต้องมานับ grid-line ใหม่)

```css
.container {
    display :grid;
    grid-template-rows: 80vh min-content 40vw repeat(3,min-content);
    grid-template-columns: [sidebar-start] 8rem [sidebar-end full-start] minmax(6rem,1fr) [center-start] repeat(8, [col-start] minmax(min-content,14rem) [col-end]) [center-end] minmax(6rem,1fr) [full-end];

    @media only screen and (max-width:$bp-large){
        // add 1 row - remove 1 st col
        grid-template-rows: 6rem 80vh min-content 40vw repeat(3,min-content);
        grid-template-columns: [sidebar-end full-start] minmax(6rem,1fr) [center-start] repeat(8, [col-start] minmax(min-content,14rem) [col-end]) [center-end] minmax(6rem,1fr) [full-end];
    }
}
```

# Note
- ยังไม่มี CSS:Selector สำหรับเลือกเฉพาะแถว,หลัก หรือเฉพาะ grid-cell
- ปัจจุบันมี subgrid แล้วแต่ยังไม่ได้ลองใช้ 