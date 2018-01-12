---
title: "Comment : définir le descripteur de Type d’un paramètre | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 78df43a5d5614c175c5134ee638a75034ced8a5d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Comment : définir le descripteur de type d'un paramètre
  Un descripteur de type contient des propriétés qui décrivent le type de données d'un paramètre. Un descripteur de type peut définir un champ, une entité ou une collection d’entités. Pour plus d’informations, consultez [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Pour définir le descripteur de type d'un paramètre  
  
1.  Dans le **détails de méthode BDC** fenêtre, choisissez le descripteur de type du paramètre.  
  
2.  Dans la barre de menus, choisissez **vue**, **fenêtre Propriétés**.  
  
3.  Dans le **propriétés** fenêtre, définissez les propriétés du descripteur de type.  
  
     Les procédures suivantes décrivent comment définir un descripteur de type en tant que champ, entité ou collection d’entités.  
  
### <a name="to-define-a-field"></a>Pour définir un champ  
  
1.  Dans le **propriétés** , configurez la **nom** propriété du descripteur de type pour le nom d’un champ dans le type qui représente l’entité (par exemple : **FirstName**).  
  
2.  Dans la liste à côté du **TypeName** propriété, choisissez le type de données approprié (par exemple, **Int32**).  
  
     Pour plus d’informations sur d’autres paramètres optionnels, consultez [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### <a name="to-define-an-entity"></a>Pour définir une entité  
  
1.  Dans le **propriétés** , configurez la **nom** propriété un nom qui décrit l’entité (par exemple : **Contact**).  
  
2.  Définir le **TypeName** propriété le nom qualifié complet du type qui représente l’entité. Ce type peut être une classe dans votre projet, un type défini dans un assembly que vous référencez dans votre solution ou un type défini dans le modèle d'objet BDC.  
  
    -   Pour une classe dans votre projet, cliquez sur la flèche bas à côté du **TypeName** propriété, choisissez le **projet actuel** onglet dans la boîte de dialogue qui s’affiche, puis choisissez la classe dans votre projet.  
  
         Le nom qualifié complet inclut l'espace de noms et le nom de la classe, suivis du nom du système LOB. L’exemple suivant définit la valeur de la **TypeName** propriété à une classe dans votre projet.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Pour un type situé dans un assembly de votre solution, le nom qualifié complet comprend le nom du type, le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.  
  
         L’exemple suivant définit la valeur de la **TypeName** propriété à un type défini dans un assembly que vous référencez dans votre solution.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Pour un type défini dans le modèle d'objet BDC, le nom qualifié complet inclut l'espace de noms et le nom du type.  
  
         L’exemple suivant définit la valeur de la **TypeName** propriété à un type dans le modèle d’objet BDC.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  Dans le **détails de méthode BDC** fenêtre, ouvrez la liste qui s’affiche pour le descripteur de type, puis choisissez **modifier**.  
  
     Le **Explorateur BDC** fenêtre s’ouvre.  
  
4.  Dans le **Explorateur BDC**, ouvrez le menu contextuel du descripteur de type, puis choisissez **ajouter un descripteur de Type**.  
  
     Un nouveau descripteur de type est ajouté en tant qu'enfant au descripteur de type d'entité. Configurez ce descripteur de type comme un champ.  
  
5.  Répétez l'étape 4 afin d'ajouter un descripteur de type enfant pour chaque champ de l'entité.  
  
### <a name="to-define-a-collection-of-entities"></a>Pour définir une collection d’entités  
  
1.  Dans le **détails de méthode BDC** fenêtre, choisissez le descripteur de type du paramètre souhaité.  
  
2.  Dans la barre de menus, choisissez **vue**, **fenêtre Propriétés**.  
  
3.  Dans le **propriétés** , configurez la **nom** propriété un nom qui décrit l’entité (par exemple : **Contacts**).  
  
4.  Définir le **IsCollection** propriété **True**. Cela indique que ce descripteur de type est une collection d’entités.  
  
5.  Définir le **TypeName** propriété dans une chaîne qui contient une référence à la <xref:System.Collections.Generic.IEnumerable%601> interface et le nom qualifié complet du type qui représente l’entité. Ce type peut être une classe dans votre projet, un type défini dans un assembly que vous référencez dans votre solution ou un type défini dans le modèle d'objet BDC.  
  
    -   Pour une classe dans votre projet, cliquez sur la flèche bas à côté du **TypeName** propriété, choisissez le **projet actuel** onglet dans la boîte de dialogue qui s’affiche, puis choisissez la classe dans votre projet.  
  
         Le nom qualifié complet inclut l'espace de noms et le nom de la classe, suivis du nom du système LOB.  
  
         L’exemple suivant définit la valeur de la **TypeName** propriété à une collection de classes dans votre projet.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1]'  
  
    -   Pour un type situé dans un assembly de votre solution, le nom qualifié complet comprend le nom du type, le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.  
  
         L’exemple suivant définit la valeur de la **TypeName** propriété à une collection de types dans un assembly que vous référencez dans votre solution.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089]'  
  
    -   Pour un type défini dans le modèle d'objet BDC, le nom qualifié complet inclut uniquement l'espace de noms et le nom du type.  
  
         L’exemple suivant définit la valeur de la **TypeName** propriété à une collection de types définis dans le modèle d’objet BDC.  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]'  
  
6.  Dans le **détails de méthode BDC** fenêtre, ouvrez la liste qui s’affiche pour le descripteur de type, puis choisissez **modifier**.  
  
     Le **Explorateur BDC** fenêtre s’ouvre.  
  
7.  Dans le **Explorateur BDC**, ouvrez le menu contextuel du descripteur de type, puis choisissez **ajouter un descripteur de Type**.  
  
     Un nouveau descripteur de type est ajouté en tant qu’enfant au descripteur de type de collection. Configurez ce descripteur de type comme une entité.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une Instance de méthode](../sharepoint/how-to-define-a-method-instance.md)   
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  