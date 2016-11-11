# 用于判断变量是 "",null,undefined.false 

    // Handle $(""), $(null), $(undefined), $(false)    
    if (!selector ) {
        return this;
    }