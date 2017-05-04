---
title: "How to: Define the Type Descriptor of a Parameter | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor"
  - "BDC [SharePoint development in Visual Studio], parameter types"
  - "BDC [SharePoint development in Visual Studio], type descriptor"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], parameter types"
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# How to: Define the Type Descriptor of a Parameter
  Un descripteur de type contient des propriétés qui décrivent le type de données d'un paramètre.  Un descripteur de type peut définir un champ, une entité ou une collection d'entités.  Pour plus d'informations, consultez [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### Pour définir le descripteur de type d'un paramètre  
  
1.  Dans la fenêtre **Détails de méthode BDC**, choisissez le descripteur de type du paramètre.  
  
2.  Dans la barre de menus, choisissez **Affichage**, **Fenêtre Propriétés**.  
  
3.  Dans la fenêtre **Propriétés**, définissez les propriétés du descripteur de type.  
  
     Les procédures suivantes décrivent comment définir un descripteur de type en tant que champ, entité ou collection d'entités.  
  
### Pour définir un champ  
  
1.  Dans la fenêtre **Propriétés**, affectez à la propriété **Name** du descripteur de type le nom d'un champ dans le type qui représente l'entité \(par exemple, FirstName\).  
  
2.  Dans la liste à côté de la propriété **TypeName**, choisissez le type de données approprié \(par exemple, **Int32**\).  
  
     Pour plus d'informations sur d'autres paramètres optionnels, consultez [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### Pour définir une entité  
  
1.  Dans la fenêtre **Propriétés**, affectez à la propriété **Name** un nom qui décrit l'entité \(par exemple, Contact\).  
  
2.  Affectez à la propriété **TypeName** le nom qualifié complet du type qui représente l'entité.  Ce type peut être une classe dans votre projet, un type défini dans un assembly que vous référencez dans votre solution ou un type défini dans le modèle d'objet BDC.  
  
    -   Pour une classe dans votre projet, cliquez sur la flèche bas qui apparaît à côté de la propriété **TypeName**, cliquez sur l'onglet **Projet actif** dans la boîte de dialogue qui apparaît, puis choisissez la classe dans votre projet.  
  
         Le nom qualifié complet inclut l'espace de noms et le nom de la classe, suivis du nom du système LOB.  L'exemple suivant affecte à la valeur de la propriété **TypeName** une classe dans votre projet.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Pour un type situé dans un assembly de votre solution, le nom qualifié complet comprend le nom du type, le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.  
  
         L'exemple suivant affecte à la valeur de la propriété **TypeName** un type défini dans un assembly que vous référencez dans votre solution.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Pour un type défini dans le modèle d'objet BDC, le nom qualifié complet inclut l'espace de noms et le nom du type.  
  
         L'exemple suivant affecte à la valeur de la propriété **TypeName** un type dans le modèle d'objet BDC.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  Dans la fenêtre **Détails de méthode BDC**, ouvrez la liste déroulante correspondant au descripteur de type, puis choisissez **Modifier**.  
  
     La fenêtre de l'**Explorateur BDC** s'ouvre.  
  
4.  Dans l'**Explorateur BDC**, ouvrez le menu contextuel du descripteur de type, puis choisissez **Ajouter un descripteur de type**.  
  
     Un nouveau descripteur de type est ajouté en tant qu'enfant au descripteur de type d'entité.  Configurez ce descripteur de type comme un champ.  
  
5.  Répétez l'étape 4 afin d'ajouter un descripteur de type enfant pour chaque champ de l'entité.  
  
### Pour définir une collection d'entités  
  
1.  Dans la fenêtre **Détails de méthode BDC**, choisissez le descripteur de type du paramètre que vous voulez.  
  
2.  Dans la barre de menus, choisissez **Affichage**, **Fenêtre Propriétés**.  
  
3.  Dans la fenêtre **Propriétés**, affectez à la propriété **Name** un nom qui décrit l'entité \(par exemple, Contacts\).  
  
4.  Affectez à la propriété **IsCollection** la valeur **True**.  Cela indique que ce descripteur de type est une collection d'entités.  
  
5.  Affectez à la propriété **TypeName** une chaîne qui contient une référence à l'interface <xref:System.Collections.Generic.IEnumerable%601>, ainsi que le nom qualifié complet du type représentant l'entité.  Ce type peut être une classe dans votre projet, un type défini dans un assembly que vous référencez dans votre solution ou un type défini dans le modèle d'objet BDC.  
  
    -   Pour une classe dans votre projet, cliquez sur la flèche bas qui apparaît à côté de la propriété **TypeName**, cliquez sur l'onglet **Projet actif** dans la boîte de dialogue qui apparaît, puis choisissez la classe dans votre projet.  
  
         Le nom qualifié complet inclut l'espace de noms et le nom de la classe, suivis du nom du système LOB.  
  
         L'exemple suivant affecte à la valeur de la propriété **TypeName** une collection de classes dans votre projet.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` `BdcModel1.Contact, BdcModel1]`  
  
    -   Pour un type situé dans un assembly de votre solution, le nom qualifié complet comprend le nom du type, le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.  
  
         L'exemple suivant affecte à la valeur de la propriété **TypeName** une collection de types dans un assembly que vous référencez dans votre solution.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`  
  
    -   Pour un type défini dans le modèle d'objet BDC, le nom qualifié complet inclut uniquement l'espace de noms et le nom du type.  
  
         L'exemple suivant affecte à la valeur de la propriété **TypeName** une collection de types définie dans le modèle d'objet BDC.  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`  
  
6.  Dans la fenêtre **Détails de méthode BDC**, ouvrez la liste déroulante correspondant au descripteur de type, puis choisissez **Modifier**.  
  
     La fenêtre de l'**Explorateur BDC** s'ouvre.  
  
7.  Dans l'**Explorateur BDC**, ouvrez le menu contextuel du descripteur de type, puis choisissez **Ajouter un descripteur de type**.  
  
     Un nouveau descripteur de type est ajouté en tant qu'enfant au descripteur de type de collection.  Configurez ce descripteur de type comme une entité.  
  
## Voir aussi  
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)   
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  