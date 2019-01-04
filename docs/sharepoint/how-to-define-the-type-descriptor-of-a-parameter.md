---
title: 'Procédure : Définir le descripteur de Type d’un paramètre | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 15b8a9dff10c88ce46ecfa5565eb9f411ce59798
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953155"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Procédure : Définir le descripteur de type d’un paramètre
  Un descripteur de type contient des propriétés qui décrivent le type de données d'un paramètre. Un descripteur de type peut définir un champ, une entité ou une collection d’entités. Pour plus d’informations, consultez [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Pour définir le descripteur de type d'un paramètre  
  
1.  Dans le **détails de méthode BDC** fenêtre, choisissez le descripteur de type du paramètre.  
  
2.  Dans la barre de menus, choisissez **vue**, **fenêtre Propriétés**.  
  
3.  Dans le **propriétés** fenêtre, définissez les propriétés du descripteur de type.  
  
     Les procédures suivantes décrivent comment définir un descripteur de type en tant que champ, entité ou collection d’entités.  
  
### <a name="to-define-a-field"></a>Pour définir un champ  
  
1.  Dans le **propriétés** fenêtre, définissez la **nom** propriété du descripteur de type pour le nom d’un champ dans le type qui représente l’entité (par exemple : **FirstName**).  
  
2.  Dans la liste à côté du **TypeName** propriété, choisissez le type de données approprié (par exemple, **Int32**).  
  
     Pour plus d’informations sur les autres paramètres facultatifs, consultez [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).  
  
### <a name="to-define-an-entity"></a>Pour définir une entité  
  
1.  Dans le **propriétés** fenêtre, définissez la **nom** propriété à un nom qui décrit l’entité (par exemple : **Contact**).  
  
2.  Définir le **TypeName** propriété le nom qualifié complet du type qui représente l’entité. Ce type peut être une classe dans votre projet, un type défini dans un assembly que vous référencez dans votre solution ou un type défini dans le modèle d'objet BDC.  
  
    -   Pour une classe dans votre projet, choisissez la flèche bas à côté du **TypeName** propriété, choisissez le **projet actuel** onglet dans la boîte de dialogue qui s’affiche, puis choisissez la classe dans votre projet.  
  
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
  
1. Dans le **détails de méthode BDC** fenêtre, choisissez le descripteur de type du paramètre que vous souhaitez.  
  
2. Dans la barre de menus, choisissez **vue**, **fenêtre Propriétés**.  
  
3. Dans le **propriétés** fenêtre, définissez la **nom** propriété à un nom qui décrit l’entité (par exemple : **Contacte**).  
  
4. Définir le **IsCollection** propriété **True**. Cela indique que ce descripteur de type est une collection d’entités.  
  
5. Définir le **TypeName** en une chaîne qui contient une référence à la <xref:System.Collections.Generic.IEnumerable%601> interface et le nom qualifié complet du type qui représente l’entité. Ce type peut être une classe dans votre projet, un type défini dans un assembly que vous référencez dans votre solution ou un type défini dans le modèle d'objet BDC.  
  
   - Pour une classe dans votre projet, choisissez la flèche bas à côté du **TypeName** propriété, choisissez le **projet actuel** onglet dans la boîte de dialogue qui s’affiche, puis choisissez la classe dans votre projet.  
  
      Le nom qualifié complet inclut l'espace de noms et le nom de la classe, suivis du nom du système LOB.  
  
      L’exemple suivant définit la valeur de la **TypeName** propriété à une collection de classes dans votre projet.  
  
      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1]'  
  
   - Pour un type situé dans un assembly de votre solution, le nom qualifié complet comprend le nom du type, le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.  
  
      L’exemple suivant définit la valeur de la **TypeName** propriété à une collection de types dans un assembly que vous référencez dans votre solution.  
  
      `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089]'  
  
   - Pour un type défini dans le modèle d'objet BDC, le nom qualifié complet inclut uniquement l'espace de noms et le nom du type.  
  
      L’exemple suivant définit la valeur de la **TypeName** propriété à une collection de types définis dans le modèle d’objet BDC.  
  
      `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]'  
  
6. Dans le **détails de méthode BDC** fenêtre, ouvrez la liste qui s’affiche pour le descripteur de type, puis choisissez **modifier**.  
  
    Le **Explorateur BDC** fenêtre s’ouvre.  
  
7. Dans le **Explorateur BDC**, ouvrez le menu contextuel du descripteur de type, puis choisissez **ajouter un descripteur de Type**.  
  
    Un nouveau descripteur de type est ajouté en tant qu’enfant au descripteur de type de collection. Configurez ce descripteur de type comme une entité.  
  
## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Guide pratique pour Ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Guide pratique pour Ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Guide pratique pour Définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)   
 [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
