# 用于判断变量是 "",null,undefined.false，0

    // Handle $(""), $(null), $(undefined), $(false) $(0)    
    if (!selector ) {
        return this;
    }