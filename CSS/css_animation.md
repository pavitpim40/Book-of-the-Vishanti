# Practice-1  : ใส่ effect ให้ sidebar

```html
 <nav class="sidebar">
    <ul class="side-nav">
        <li class="side-nav__item side-nav__item--active">
            <a href="#" class="side-nav__link">
                <svg class="side-nav__icon">
                    <use xlink:href="img/sprite.svg#icon-home"></use>
                </svg>
                <span>Hotel</span>
            </a>
        </li>
    </ul>
</nav>

```

```scss
.side-nav {
  
    // each li
    &__item::before{
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        height: 100%;
        width: 3px;
        background-color: var(--color-primary);
        transform: scaleY(0);
        transition: transform 0.2s, 
                    width 0.4s cubic-bezier(1,0,0,1) 0.2s,
                    background-color .1s;
    }

    &__item:hover::before,
    &__item--active::before {
        transform: scaleY(1);
        width: 100%;
    }

    &__item:active::before {
        background-color: var(--color-primary-light);
    }
}


```