---
title: Guide pratique pour créer des types à l'aide du Concepteur de classes
description: Apprenez à concevoir de nouveaux types pour les projets C# et Visual Basic en les créant sur un diagramme de classes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6102d5252564834f1de7c533e763d7b08a8f9fb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880539"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Guide pratique pour créer des types à l’aide du Concepteur de classes

Pour concevoir de nouveaux types pour les projets C# et Visual Basic, créez-les dans un diagramme de classes. Pour visualiser les types existants, consultez [Guide pratique pour afficher les types existants](how-to-view-existing-types.md).

## <a name="create-a-new-type"></a><a name="CreateType"></a> Créer un nouveau type

1. Dans la **Boîte à outils**, sous **Concepteur de classes**, faites glisser l’un des éléments ci-dessous dans un diagramme de classes :

    - **Classe** ou **Classe abstraite**

    - **Enum**

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

     Consultez [Création de membres](creating-and-configuring-type-members.md#create-members).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Appliquer un attribut personnalisé à un type

1. Cliquez sur la forme du type sur un diagramme de classes.

2. Dans **Propriétés**, cliquez sur le bouton de sélection (...) situé à côté de la propriété **Attributs personnalisés**.

3. Ajoutez un ou plusieurs attributs personnalisés, un par ligne. Ne les placez pas entre crochets.

   Les attributs personnalisés sont appliqués au type.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Appliquer un attribut personnalisé à un membre de type

1. Cliquez sur le nom du membre dans la forme de son type sur un diagramme de classes ou sur sa ligne dans la fenêtre Détails de classe.

2. Dans **Propriétés**, recherchez la propriété **Attributs personnalisés** du membre.

3. Ajoutez un ou plusieurs attributs personnalisés, un par ligne. Ne les placez pas entre crochets.

   Les attributs personnalisés sont appliqués au type.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer l’héritage entre les types](how-to-create-inheritance-between-types.md)
- [Guide pratique pour créer des associations entre des types](how-to-create-associations-between-types.md)
- [Création et configuration de membres de type](creating-and-configuring-type-members.md)
- [Conception des classes et des types](designing-and-viewing-classes-and-types.md)
