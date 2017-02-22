---
title: "How to: Create Types by using Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Clr.ClrAttributesDialog"
helpviewer_keywords: 
  - "custom attributes, applying"
  - "class diagrams, creating types"
  - "classes [Visual Studio], creating with Class Designer"
  - "Class Designer [Visual Studio], creating classes"
  - "types [Visual Studio], class diagrams"
  - "attributes [Visual Studio], applying custom"
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# How to: Create Types by using Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour concevoir de nouveaux types pour les projets Visual C\# .NET et Visual Basic .NET, créez\-les dans un diagramme de classes.  Pour voir les types existants, consultez [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md).  
  
-   [Créer un nouveau type](#CreateType)  
  
-   [Appliquer un attribut personnalisé à un type](#CustAttributeType)  
  
-   [Appliquer un attribut personnalisé à un membre de type](#CustAttributeMember)  
  
##  <a name="CreateType"></a> Créer un nouveau type  
  
1.  Dans la boîte à outils, sous Concepteur de classes, faites glisser l'un des éléments ci\-dessous dans un diagramme de classes :  
  
    -   **Classe** ou **Classe abstraite**  
  
    -   **Enum**  
  
    -   **Interface**  
  
    -   **Structure** \(VB\) ou **Struct** \(C\#\)  
  
    -   **Délégué**  
  
    -   **Module** \(VB uniquement\)  
  
2.  Nommez le type.  Sélectionnez ensuite son niveau d'accès.  
  
3.  Sélectionnez le fichier dans lequel vous souhaitez ajouter le code initial pour le type :  
  
    -   Pour créer un fichier et l'ajouter au projet actuel, sélectionnez **Créer un nouveau fichier** et nommez\-le.  
  
    -   Pour ajouter du code à un fichier existant, sélectionnez **Ajouter au fichier existant**.  
  
         Si votre solution possède un projet qui partage du code dans plusieurs applications, vous pouvez ajouter un nouveau type à un diagramme de classes dans le projet d'application, mais uniquement si le fichier de classe correspondant se trouve dans le même projet d'application ou dans le projet partagé.  
  
4.  Ajoutez à présent d'autres éléments pour définir le type :  
  
    |||  
    |-|-|  
    |**Pour les éléments suivants**|**Ajouter**|  
    |Classes, classes abstraites, structures ou structs|Méthodes, propriétés, champs, événements, constructeurs \(méthode\), destructeurs \(méthode\) et constantes qui définissent le type|  
    |Enums|Valeurs de champ qui composent l'énumération|  
    |Interfaces|Méthodes, propriétés et événements qui composent l'interface|  
    |Délégué|Paramètres qui définissent le délégué|  
    |Module|Méthodes, propriétés, champs, événements, constructeurs \(méthode\) et constantes qui définissent le module|  
  
     Consultez [Création de membres](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a> Appliquer un attribut personnalisé à un type  
  
1.  Cliquez sur la forme du type sur un diagramme de classes.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le bouton de sélection \(...\), situé à côté de la propriété **Custom Attributes**.  
  
3.  Ajoutez un ou plusieurs attributs personnalisés, un par ligne.  Ne les placez pas entre crochets.  
  
     Une fois que vous avez terminé, les attributs personnalisés sont appliqués au type.  
  
##  <a name="CustAttributeMember"></a> Appliquer un attribut personnalisé à un membre de type  
  
1.  Cliquez sur le nom du membre dans la forme de son type sur un diagramme de classes ou sur sa ligne dans la fenêtre Détails de classe.  
  
2.  Dans la fenêtre Propriétés, recherchez la propriété **Attributs personnalisés** du membre.  
  
3.  Ajoutez un ou plusieurs attributs personnalisés, un par ligne.  Ne les placez pas entre crochets.  
  
     Une fois que vous avez terminé, les attributs personnalisés sont appliqués au type.  
  
## Voir aussi  
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Creating and Configuring Type Members \(Class Designer\)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)