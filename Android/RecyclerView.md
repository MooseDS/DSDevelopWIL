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

