---
title: Guide pratique pour créer des types à l’aide du Concepteur de classes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f87e3a3adda270f6b78b9134c7535bda6c73d952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533144"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Guide pratique pour créer des types à l'aide du Concepteur de classes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour concevoir de nouveaux types pour les projets Visual C# .NET et Visual Basic .NET, créez-les dans un diagramme de classes. Pour visualiser les types existants, consultez [Guide pratique pour afficher les types existants (Concepteur de classes)](../ide/how-to-view-existing-types-class-designer.md).

- [Créer un nouveau type](#CreateType)

- [Appliquer un attribut personnalisé à un type](#CustAttributeType)

- [Appliquer un attribut personnalisé à un membre de type](#CustAttributeMember)

## <a name="create-a-new-type"></a><a name="CreateType"></a> Créer un nouveau type

1. Dans la boîte à outils, sous Concepteur de classes, faites glisser l'un des éléments ci-dessous dans un diagramme de classes :

    - **Classe** ou **Classe abstraite**

    - **Énumération**

    - **Interface**

    - **Structure** (VB) ou **Struct** (C#)

    - **Délégué**

    - **Module** (VB uniquement)

2. Nommez le type. Sélectionnez ensuite son niveau d'accès.

3. Sélectionnez le fichier dans lequel vous souhaitez ajouter le code initial pour le type :

    - Pour créer un fichier et l’ajouter au projet actuel, sélectionnez **Créer un nouveau fichier** et nommez le fichier.

    - Pour ajouter du code à un fichier existant, sélectionnez **Ajouter au fichier existant**.

         Si votre solution possède un projet qui partage du code dans plusieurs applications, vous pouvez ajouter un nouveau type à un diagramme de classes dans le projet d'application, mais uniquement si le fichier de classe correspondant se trouve dans le même projet d'application ou dans le projet partagé.

4. Ajoutez à présent d'autres éléments pour définir le type :

    |**Pour**|**Ajouter**|
    |-|-|
    |Classes, classes abstraites, structures ou structs|Méthodes, propriétés, champs, événements, constructeurs (méthode), destructeurs (méthode) et constantes qui définissent le type|
    |Énumérations|Valeurs de champ qui composent l'énumération|
    |Interfaces|Méthodes, propriétés et événements qui composent l'interface|
    |Délégué|Paramètres qui définissent le délégué|
    |Module|Méthodes, propriétés, champs, événements, constructeurs (méthode) et constantes qui définissent le module|

     Consultez [Création de membres](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Appliquer un attribut personnalisé à un type

1. Cliquez sur la forme du type sur un diagramme de classes.

2. Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (...) situé à côté de la propriété **Attributs personnalisés**.

3. Ajoutez un ou plusieurs attributs personnalisés, un par ligne. Ne les placez pas entre crochets.

     Une fois que vous avez terminé, les attributs personnalisés sont appliqués au type.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Appliquer un attribut personnalisé à un membre de type

1. Cliquez sur le nom du membre dans la forme de son type sur un diagramme de classes ou sur sa ligne dans la fenêtre Détails de classe.

2. Dans la fenêtre Propriétés, recherchez la propriété **Attributs personnalisés** du membre.

3. Ajoutez un ou plusieurs attributs personnalisés, un par ligne. Ne les placez pas entre crochets.

     Une fois que vous avez terminé, les attributs personnalisés sont appliqués au type.

## <a name="see-also"></a>Voir aussi
 [Comment : créer un héritage entre des types (Concepteur de classes)](../ide/how-to-create-inheritance-between-types-class-designer.md) [Comment : créer des associations entre des types (Concepteur de classes)](../ide/how-to-create-associations-between-types-class-designer.md) [création et configuration de membres de type (Concepteur de classes)](../ide/creating-and-configuring-type-members-class-designer.md) [utilisation de diagrammes de classes (Concepteur de classes)](../ide/working-with-class-diagrams-class-designer.md) [conception de classes et de types (Concepteur de classes)](../ide/designing-classes-and-types-class-designer.md)
