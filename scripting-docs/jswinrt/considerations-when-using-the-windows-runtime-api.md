---
title: "Consid&#233;rations relatives &#224; l&#39;utilisation de l&#39;API Windows Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, API Windows Runtime."
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Consid&#233;rations relatives &#224; l&#39;utilisation de l&#39;API Windows Runtime
Utilisez presque chaque élément de l'API Windows Runtime dans JavaScript.  Toutefois, vous ne devez pas oublier certains aspects de la représentation JavaScript d'éléments de Windows Runtime.  
  
> [!IMPORTANT]
>  Pour plus d'informations sur la création de composants Windows Runtime dans C\+\+, C\#, ou Visual Basic et leur utilisation dans JavaScript, consultez [Création de composants Windows Runtime](http://msdn.microsoft.com/library/9a6b8f0a-7d5e-40a0-a9c5-a59b4908e133).  
  
## Cas particuliers de la représentation JavaScript des types Windows Runtime  
  
-   Chaînes : une chaîne non initialisée est passée à une méthode Windows Runtime en tant que chaîne « undefined », et une chaîne dont la valeur est `null` est passée en tant que chaîne « null ». \(C'est le cas lorsqu'une valeur `null` ou `undefined` est convertie en chaîne.\) Avant de passer une chaîne à une méthode Windows Runtime, elle doit être initialisée en chaîne vide \(« »\).  
  
-   Interfaces : vous ne pouvez pas implémenter une interface Windows Runtime dans JavaScript.  
  
-   Tableaux : les tableaux Windows Runtime ne sont pas redimensionnables. Les méthodes de redimensionnement des tableaux dans JavaScript ne s'appliquent pas pour les tableaux Windows Runtime.  
  
-   Tableaux : si vous passez une valeur de tableau JavaScript à une méthode Windows Runtime, le tableau est copié.  Le tableau ou ses membres ne peuvent pas être modifiés par la méthode Windows Runtime et sont retournés à votre application JavaScript.  Toutefois, vous pouvez utiliser les tableaux typés \(par exemple, [Int32Array, objet](../javascript/reference/int32array-object.md)\), qui ne sont pas copiés.  
  
-   Structures : les structures Windows Runtime sont des objets dans JavaScript.  Si vous souhaitez passer une structure Windows Runtime à une méthode Windows Runtime, n'instanciez pas la structure avec le mot clé `new` .  Créez plutôt un objet et ajoutez les membres pertinents et leurs valeurs.  Les noms des membres doivent être dans la casse mixte : `SomeStruct.firstMember`.  
  
-   Objets : les objets JavaScript ne sont pas identiques aux objets de code managé \(`System.Object`\).  Vous ne pouvez pas passer un objet JavaScript à une méthode Windows Runtime qui requiert un `System.Object`.  
  
-   Identité d'objet : dans la plupart des cas, les objets passés entre Windows Runtime et JavaScript ne sont pas modifiés.  Le moteur JavaScript garde un mappage des objets connus.  Lorsqu'un objet est retourné par Windows Runtime, il est comparé au mappage, et s'il n'existe pas, un nouvel objet est créé.  La même procédure est appliquée pour les objets qui représentent les interfaces qui sont retournées par Windows Runtime.  Il existe deux types d'exceptions :  
  
    -   Les objects retournés d'un appel Windows Runtime, et ont alors une nouvelle propriété ajoutée \(expando\), ne conservent pas ces propriétés lorsqu'ils sont repassés au Windows Runtime.  Toutefois, lorsqu'ils sont retournés à l'application JavaScript, les objets retournés n'ont pas de propriété expando car ils sont mis en correspondance avec l'objet existant.  
  
    -   Les structures et les délégués ne peuvent pas être identifiés dans Windows Runtime comme étant identiques aux structures ou aux délégués précédemment utilisés.  Chaque fois qu'une structure ou un délégué est retourné, il se voit attribué une nouvelle référence.  
  
-   Collisions de noms : de multiples interfaces Windows Runtime peuvent avoir des membres portant le même nom.  S'ils sont combinés dans un seul objet JavaScript \(qui peut être une représentation d'une classe d'exécution ou d'une interface\), les membres sont représentés avec des noms complets.  Ces membres peuvent être appelés à l'aide de la syntaxe suivante : `Class["MemberName"](parameter)`.  
  
     Dans le code suivant, deux interfaces ont une méthode Draw, et une classe d'exécution implémente les deux interfaces.  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     Voici comment appeler le code ci\-dessus dans JavaScript.  
  
    ```javascript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   Les paramètres `Out` : si une méthode Windows Runtime a plusieurs paramètres `out`, dans JavaScript, la méthode possède un objet JavaScript comme valeur de retour, et l'objet a des propriétés qui correspondent au paramètre `out`.  Prenons par exemple la signature Windows Runtime dans C\+\+.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     La version JavaScript de cette signature est :  
  
    ```javascript  
    var returnValue = exampleMethod();  
  
    ```  
  
     Dans cet exemple, `returnValue` est un objet JavaScript à deux champs : `first` et `second`.  
  
-   Membres statiques : Windows Runtime définit à la fois les membres statiques et les membres d'instance.  Dans JavaScript, des membres statiques sont ajoutés à l'objet associé à la classe ou à l'interface Windows Runtime.  
  
    ```javascript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Pour plus d'informations sur les représentations JavaScript des types de base Windows Runtime, consultez [Représentation JavaScript des types Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md).