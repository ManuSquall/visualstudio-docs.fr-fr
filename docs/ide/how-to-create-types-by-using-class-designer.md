---
title: "Guide pratique pour créer des types à l’aide du Concepteur de classes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf8691e4e38ae19aa1e8e04257f208241c02efac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-types-by-using-class-designer"></a>Guide pratique pour créer des types à l'aide du Concepteur de classes
Pour concevoir de nouveaux types pour les projets Visual C# .NET et Visual Basic .NET, créez-les dans un diagramme de classes. Pour visualiser les types existants, consultez [Guide pratique pour afficher les types existants (Concepteur de classes)](../ide/how-to-view-existing-types-class-designer.md).  
  
-   [Créer un nouveau type](#CreateType)  
  
-   [Appliquer un attribut personnalisé à un type](#CustAttributeType)  
  
-   [Appliquer un attribut personnalisé à un membre de type](#CustAttributeMember)  
  
##  <a name="CreateType"></a> Créer un nouveau type  
  
1.  Dans la boîte à outils, sous Concepteur de classes, faites glisser l'un des éléments ci-dessous dans un diagramme de classes :  
  
    -   **Classe** ou **Classe abstraite**  
  
    -   **Enum**  
  
    -   **Interface**  
  
    -   **Structure** (VB) ou **Struct** (C#)  
  
    -   **Delegate**  
  
    -   **Module** (VB uniquement)  
  
2.  Nommez le type. Sélectionnez ensuite son niveau d'accès.  
  
3.  Sélectionnez le fichier dans lequel vous souhaitez ajouter le code initial pour le type :  
  
    -   Pour créer un fichier et l’ajouter au projet actuel, sélectionnez **Créer un nouveau fichier** et nommez le fichier.  
  
    -   Pour ajouter du code à un fichier existant, sélectionnez **Ajouter au fichier existant**.  
  
         Si votre solution possède un projet qui partage du code dans plusieurs applications, vous pouvez ajouter un nouveau type à un diagramme de classes dans le projet d'application, mais uniquement si le fichier de classe correspondant se trouve dans le même projet d'application ou dans le projet partagé.  
  
4.  Ajoutez à présent d'autres éléments pour définir le type :  
  
    |||  
    |-|-|  
    |**Pour**|**Ajouter**|  
    |Classes, classes abstraites, structures ou structs|Méthodes, propriétés, champs, événements, constructeurs (méthode), destructeurs (méthode) et constantes qui définissent le type|  
    |Enums|Valeurs de champ qui composent l'énumération|  
    |Interfaces|Méthodes, propriétés et événements qui composent l'interface|  
    |Délégué|Paramètres qui définissent le délégué|  
    |Module|Méthodes, propriétés, champs, événements, constructeurs (méthode) et constantes qui définissent le module|  
  
     Consultez [Création de membres](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a> Appliquer un attribut personnalisé à un type  
  
1.  Cliquez sur la forme du type sur un diagramme de classes.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (...) situé à côté de la propriété **Attributs personnalisés**.  
  
3.  Ajoutez un ou plusieurs attributs personnalisés, un par ligne. Ne les placez pas entre crochets.  
  
     Une fois que vous avez terminé, les attributs personnalisés sont appliqués au type.  
  
##  <a name="CustAttributeMember"></a> Appliquer un attribut personnalisé à un membre de type  
  
1.  Cliquez sur le nom du membre dans la forme de son type sur un diagramme de classes ou sur sa ligne dans la fenêtre Détails de classe.  
  
2.  Dans la fenêtre Propriétés, recherchez la propriété **Attributs personnalisés** du membre.  
  
3.  Ajoutez un ou plusieurs attributs personnalisés, un par ligne. Ne les placez pas entre crochets.  
  
     Une fois que vous avez terminé, les attributs personnalisés sont appliqués au type.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour créer l’héritage entre les types (Concepteur de classes)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Guide pratique pour créer des associations entre les types (Concepteur de classes)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Création et configuration de membres de type (Concepteur de classes)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [Utilisation des diagrammes de classes (Concepteur de classes)](../ide/working-with-class-diagrams-class-designer.md)   
 [Conception des classes et des types (Concepteur de classes)](../ide/designing-classes-and-types-class-designer.md)