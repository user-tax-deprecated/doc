gif 动画批量转 webp

fd '.gif' -x bash -c 'gif2webp $1 -o $1.webp -mixed -lossy -min_size -kmax 5 -kmin 3' bash
