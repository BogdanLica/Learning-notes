## Basics

###### Flex container properties
* putting an element/class into a container : **display : flex;** 
* allign any children of that element into rows or columns by using the **flex-direction:**
* allign and specify the spacing between containers using **justify-content**
* simmilar to the *justify-content* is the **align-items** (the former is used for the main axis/horizontal and the latter for the cross axis/vertical)
* wrapping elements means extra element can be moved to a new row or column using the **flex-wrap**

###### Flex item properties
* if the parent's width is smaller than the combinet width of its items, an item can use the **flex-shrink** to reduce the size of an item compared to the size of others
* to expand an item use **flex-grow**
* setting the size of an item before using the shrink and grow properties is done with the **flex-basis**
* to specify the order of an item in the container use the **order** property
* to set the align of an individual item use **align-self**