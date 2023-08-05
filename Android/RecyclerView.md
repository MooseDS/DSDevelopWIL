# RecyclerView 유용한 Tip

### Single Item Select

~~~
var selectedItemPos = -1
var lastItemSelectedPos = -1

inner class viewHolder {
    init {
        setOnClickListener {
            selectedItemPos = bindingAdapterPosition
            lastItemSelectedPos = if(lastItemSelectedPos == -1)
                selectedItemPos
            else {
                notifyItemChanged(lastItemSelectedPos)
                selectedItemPos
            }
            notifyItemChanged(selectedItemPos)
        }
    }
}

override onBindViewHolder(holder: ViewHolder, positon: Int) {
    if (position == selectItemPos) {
        // TODO 
    } else {
        // TODO 
    }
}

~~~

---

### PagingSource 

ISSUE 

1. 매개변수를 StateFlow 객체를 통해 받아야 할 경우
2. PagingData 일부 데이터를 임시저장해야 할 경우
