# 工厂（FactoryPattern）模式

## 简介

工厂模式是Java中最常用的设计模式之一。 

这种类型的设计模式属于创建模式，因为此模式提供了创建对象的最佳方法之一。 

在工厂模式中，我们没有创建逻辑暴露给客户端创建对象，并使用一个通用的接口引用新创建的对象。

## 实现

1. 创建一个接口：

Shape.java

```java
public interface Shape {
   void draw();
}
```

2. 创建实现相同接口的具体类。如下所示几个类：

Rectangle.java 

```java
public class Rectangle implements Shape {

   @Override
   public void draw() {
      System.out.println("Inside Rectangle::draw() method.");
   }
}
```

Square.java 

```java
public class Square implements Shape {

   @Override
   public void draw() {
      System.out.println("Inside Square::draw() method.");
   }
}
```

Circle.java

```java
public class Circle implements Shape {

   @Override
   public void draw() {
      System.out.println("Inside Circle::draw() method.");
   }
}
```

3. 创建工厂根据给定的信息生成具体类的对象：

ShapeFactory.java

```java
public class ShapeFactory {

   //use getShape method to get object of type shape 
   public Shape getShape(String shapeType){
      if(shapeType == null){
         return null;
      }        
      if(shapeType.equalsIgnoreCase("CIRCLE")){
         return new Circle();

      } else if(shapeType.equalsIgnoreCase("RECTANGLE")){
         return new Rectangle();

      } else if(shapeType.equalsIgnoreCase("SQUARE")){
         return new Square();
      }

      return null;
   }
}
```

4. 使用工厂通过传递类型等信息来获取具体类的对象：

FactoryPatternDemo.java 

```java
public class FactoryPatternDemo {

   public static void main(String[] args) {
      ShapeFactory shapeFactory = new ShapeFactory();

      //get an object of Circle and call its draw method.
      Shape shape1 = shapeFactory.getShape("CIRCLE");

      //call draw method of Circle
      shape1.draw();

      //get an object of Rectangle and call its draw method.
      Shape shape2 = shapeFactory.getShape("RECTANGLE");

      //call draw method of Rectangle
      shape2.draw();

      //get an object of Square and call its draw method.
      Shape shape3 = shapeFactory.getShape("SQUARE");

      //call draw method of circle
      shape3.draw();
   }
}
```

5. 验证输出结果如下：

```
Inside Circle::draw() method.
Inside Rectangle::draw() method.
Inside Square::draw() method.
```
