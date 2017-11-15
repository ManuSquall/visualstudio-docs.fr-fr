---
title: "Considérations sur l’utilisation de l’API Windows Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="considerations-when-using-the-windows-runtime-api"></a>Considérations sur l’utilisation de l’API Windows Runtime
Vous pouvez utiliser presque tous les éléments de l’API Windows Runtime en JavaScript. Toutefois, vous devez prendre en compte certains aspects de la représentation JavaScript des éléments Windows Runtime.  
  
> [!IMPORTANT]
>  Pour obtenir des informations sur la création de composants Windows Runtime en C++, C# ou Visual Basic et leur utilisation dans JavaScript, consultez [Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) et [Création de composants Windows Runtime en C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Cas particuliers de la représentation JavaScript des types Windows Runtime  
  
-   Chaînes : une chaîne non initialisée est passée à une méthode Windows Runtime comme chaîne « undefined », tandis qu’une chaîne `null` est passée comme chaîne « null ». (Cela est vrai chaque fois qu’une valeur `null` ou `undefined` est forcée en type chaîne.) Avant de passer une chaîne à une méthode Windows Runtime, vous devez l’initialiser comme chaîne vide ("").  
  
-   Interfaces : vous ne pouvez pas implémenter une interface Windows Runtime dans JavaScript.  
  
-   Tableaux : les tableaux Windows Runtime ne sont pas redimensionnables. Les méthodes qui redimensionnement des tableaux dans JavaScript ne fonctionnent donc pas sur les tableaux Windows Runtime.  
  
-   Tableaux : si vous passez une valeur de tableau JavaScript à une méthode Windows Runtime, le tableau est copié. La méthode Windows Runtime ne peut pas modifier le tableau ou ses membres et les retourner à votre application JavaScript. Toutefois, vous pouvez utiliser des tableaux typés (par exemple, l’[objet Int32Array](../javascript/reference/int32array-object.md)), qui ne sont pas copiés.  
  
-   Structures : les structures Windows Runtime sont des objets dans JavaScript. Si vous souhaitez passer une structure Windows Runtime à une méthode Windows Runtime, n’instanciez pas la structure avec le mot clé `new`. Au lieu de cela, créez un objet et ajoutez les membres concernés et leurs valeurs. Les noms des membres doivent être en casse mixte : `SomeStruct.firstMember`.  
  
-   Objets : les objets JavaScript ne sont pas les mêmes que ceux en code managé (`System.Object`). Vous ne pouvez pas passer un objet JavaScript à une méthode Windows Runtime qui nécessite un `System.Object`.  
  
-   Identité de l’objet : dans la plupart des cas, les objets qui sont passés entre le Windows Runtime et JavaScript ne changent pas. Le moteur JavaScript gère un mappage d’objets connus. Quand un objet est retourné par le Windows Runtime, il est comparé au mappage et, s’il n’existe pas, un objet est créé. La même procédure est appliquée pour les objets qui représentent des interfaces retournées par les méthodes Windows Runtime. Il existe deux types d’exceptions :  
  
    -   Les objets retournés par un appel Windows Runtime, et auxquels de nouvelles propriétés (expando) sont ensuite ajoutées, ne conservent pas leurs nouvelles propriétés quand ils sont repassés au Windows Runtime. Toutefois, quand ils sont retournés à l’application JavaScript, dans la mesure où ils sont mappés à l’objet existant, l’objet retourné a les propriétés expando.  
  
    -   Les structures et les délégués dans Windows Runtime ne peuvent pas être identifiés comme étant identiques aux structures ou délégués précédemment utilisés. Chaque fois qu’une structure ou un délégué est retourné, il obtient une nouvelle référence.  
  
-   Collisions de noms : plusieurs interfaces Windows Runtime peuvent avoir des membres portant le même nom. Si elles sont combinées dans un seul objet JavaScript (qui peut être une représentation d’une interface ou d’une classe runtime), les membres sont représentés par des noms complets. Vous pouvez appeler ces membres à l’aide de la syntaxe suivante : `Class["MemberName"](parameter)`.  
  
     Dans le code suivant, deux interfaces ont une méthode Draw, et une classe runtime implémente les deux interfaces.  
  
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
  
     Voici comment vous pouvez appeler le code ci-dessus en JavaScript.  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   Paramètres `Out` : prenez une méthode Windows Runtime avec plusieurs paramètres `out`. En JavaScript, la méthode a un objet JavaScript comme valeur de retour, et l’objet a des propriétés qui correspondent au paramètre `out`. Par exemple, considérez la signature Windows Runtime suivante en C++.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     La version JavaScript de cette signature est la suivante :  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     Dans cet exemple, `returnValue` est un objet JavaScript avec deux champs : `first` et `second`.  
  
-   Membres statiques : le Windows Runtime définit les membres statiques et les membres d’instance. En JavaScript, les membres statiques sont ajoutés à l’objet qui est associé à l’interface ou à la classe Windows Runtime.  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Pour plus d’informations sur la représentation JavaScript des types de base Windows Runtime, consultez [Représentation JavaScript des types Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md).