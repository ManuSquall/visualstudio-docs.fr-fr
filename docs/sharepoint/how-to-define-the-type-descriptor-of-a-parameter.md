---
title: 'Comment : définir le descripteur de type d’un paramètre | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0b3ae803576c98a86a45d175af45aa28b3852134
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016849"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Comment : définir le descripteur de type d’un paramètre
  Un descripteur de type contient des propriétés qui décrivent le type de données d'un paramètre. Un descripteur de type peut définir un champ, une entité ou une collection d’entités. Pour plus d’informations, consultez [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Pour définir le descripteur de type d'un paramètre

1. Dans la fenêtre **Détails de méthode BDC** , choisissez le descripteur de type du paramètre.

2. Dans la barre de menus, choisissez **affichage**, **fenêtre Propriétés**.

3. Dans la fenêtre **Propriétés** , définissez les propriétés du descripteur de type.

     Les procédures suivantes décrivent comment définir un descripteur de type en tant que champ, entité ou collection d'entités.

### <a name="to-define-a-field"></a>Pour définir un champ

1. Dans la fenêtre **Propriétés** , définissez la propriété **Name** du descripteur de type sur le nom d’un champ du type qui représente l’entité (par exemple : **FirstName**).

2. Dans la liste en regard de la propriété **TypeName** , choisissez le type de données approprié (par exemple, **Int32**).

     Pour plus d’informations sur les autres paramètres facultatifs, consultez [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>Pour définir une entité

1. Dans la fenêtre **Propriétés** , affectez à la propriété **Name** un nom qui décrit l’entité (par exemple : **contact**).

2. Affectez à la propriété **TypeName** le nom qualifié complet du type qui représente l’entité. Ce type peut être une classe dans votre projet, un type défini dans un assembly que vous référencez dans votre solution ou un type défini dans le modèle d'objet BDC.

    - Pour une classe de votre projet, cliquez sur la flèche vers le bas en regard de la propriété **TypeName** , choisissez l’onglet **projet actif** dans la boîte de dialogue qui s’affiche, puis choisissez la classe dans votre projet.

         Le nom qualifié complet inclut l'espace de noms et le nom de la classe, suivis du nom du système LOB. L’exemple suivant affecte à la valeur de la propriété **TypeName** une classe de votre projet.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Pour un type situé dans un assembly de votre solution, le nom qualifié complet comprend le nom du type, le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.

         L’exemple suivant affecte à la valeur de la propriété **TypeName** un type défini dans un assembly que vous référencez dans votre solution.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - Pour un type défini dans le modèle d'objet BDC, le nom qualifié complet inclut l'espace de noms et le nom du type.

         L’exemple suivant affecte à la valeur de la propriété **TypeName** un type dans le modèle d’objet BDC.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. Dans la fenêtre **Détails de méthode BDC** , ouvrez la liste qui s’affiche pour le descripteur de type, puis choisissez **modifier**.

     La fenêtre de l' **Explorateur BDC** s’ouvre.

4. Dans l' **Explorateur BDC**, ouvrez le menu contextuel du descripteur de type, puis choisissez **Ajouter un descripteur de type**.

     Un nouveau descripteur de type est ajouté en tant qu'enfant au descripteur de type d'entité. Configurez ce descripteur de type comme un champ.

5. Répétez l'étape 4 afin d'ajouter un descripteur de type enfant pour chaque champ de l'entité.

### <a name="to-define-a-collection-of-entities"></a>Pour définir une collection d'entités

1. Dans la fenêtre **Détails de méthode BDC** , choisissez le descripteur de type du paramètre de votre choix.

2. Dans la barre de menus, choisissez **affichage**, **fenêtre Propriétés**.

3. Dans la fenêtre **Propriétés** , affectez à la propriété **Name** un nom qui décrit l’entité (par exemple : **contacts**).

4. Affectez à la propriété **IsCollection** la **valeur true**. Cela indique que ce descripteur de type est une collection d'entités.

5. Affectez à la propriété **TypeName** une chaîne qui contient une référence à l' <xref:System.Collections.Generic.IEnumerable%601> interface et le nom qualifié complet du type qui représente l’entité. Ce type peut être une classe dans votre projet, un type défini dans un assembly que vous référencez dans votre solution ou un type défini dans le modèle d'objet BDC.

   - Pour une classe de votre projet, cliquez sur la flèche vers le bas en regard de la propriété **TypeName** , choisissez l’onglet **projet actif** dans la boîte de dialogue qui s’affiche, puis choisissez la classe dans votre projet.

      Le nom qualifié complet inclut l'espace de noms et le nom de la classe, suivis du nom du système LOB.

      L’exemple suivant affecte à la valeur de la propriété **TypeName** une collection de classes dans votre projet.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace. BdcModel1. contact, BdcModel1] '

   - Pour un type situé dans un assembly de votre solution, le nom qualifié complet comprend le nom du type, le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.

      L’exemple suivant affecte à la valeur de la propriété **TypeName** une collection de types dans un assembly que vous référencez dans votre solution.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace. contact, myAssemblyName, version = 4.0.0.0, culture = neutral, PublicKeyToken = b77a5c561934e089] '

   - Pour un type défini dans le modèle d'objet BDC, le nom qualifié complet inclut uniquement l'espace de noms et le nom du type.

      L’exemple suivant affecte à la valeur de la propriété **TypeName** une collection de types définie dans le modèle d’objet BDC.

      `System.Collections.Generic.IEnumerable`1 [Microsoft. BusinessData. Runtime. DynamicType] '

6. Dans la fenêtre **Détails de méthode BDC** , ouvrez la liste qui s’affiche pour le descripteur de type, puis choisissez **modifier**.

    La fenêtre de l' **Explorateur BDC** s’ouvre.

7. Dans l' **Explorateur BDC**, ouvrez le menu contextuel du descripteur de type, puis choisissez **Ajouter un descripteur de type**.

    Un nouveau descripteur de type est ajouté en tant qu’enfant au descripteur de type de collection. Configurez ce descripteur de type comme une entité.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
