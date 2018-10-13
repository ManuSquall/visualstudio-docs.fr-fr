---
title: 'Comment : configurer l’héritage à l’aide du Concepteur O-R | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a6c8e4b2da87185c41157b8d03bd59b37188a43
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222688"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Comment : configurer l’héritage à l’aide du Concepteur O/R
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) prend en charge le concept d'héritage à table unique qui est souvent implémenté dans les systèmes relationnels. L'héritage à table unique fait appel à une seule table de base de données qui contient des champs pour les informations parent et enfant. Avec les données relationnelles, une colonne de discriminateur contient la valeur qui détermine à quelle classe tout enregistrement appartient.  
  
 Prenons par exemple une table Persons qui contient tous les employées d'une société. Certaines personnes sont des employés et d'autres des responsables. La table Persons contient une colonne nommée `EmployeeType` qui a une valeur de 1 pour les responsables et une valeur de 2 pour les employés ; c'est la colonne de discriminateur. Dans ce scénario, vous pouvez créer une sous-classe d'employés et remplir la classe avec uniquement des enregistrements ayant une valeur `EmployeeType` de 2. Vous pouvez également supprimer les colonnes qui ne s'appliquent à aucune de ces classes.  
  
 La création d'un modèle objet qui utilise l'héritage (et correspond aux données relationnelles) peut prêter à confusion. La procédure suivante esquisse les étapes requises pour configurer l'héritage avec le Concepteur O/R. Suivre les étapes génériques sans faire référence à une table existante et aux colonnes risque d'être difficile, c'est pourquoi une procédure pas à pas utilisant des données vous est proposée. Pour obtenir des instructions détaillées pour configurer l’héritage à l’aide de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], consultez [procédure pas à pas : création de Classes LINQ to SQL par héritage à Table unique (Concepteur O/R) à l’aide de](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### <a name="to-create-inherited-data-classes"></a>Pour créer des classes de données héritées  
  
1.  Ouvrez le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] en ajoutant un **Classes LINQ to SQL** élément à un projet Visual Basic ou c# existant.  
  
2.  Faites glisser la table à utiliser comme classe de base vers le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
3.  Faites glisser une deuxième copie de la table sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] et renommez-la. C'est la classe dérivée, ou sous-classe.  
  
4.  Cliquez sur **héritage** dans le **concepteur objet/relationnel** onglet de la **boîte à outils**, puis cliquez sur la sous-classe (la table que vous avez renommé) et connectez-la à la classe de base.  
  
    > [!NOTE]
    >  Cliquez sur le **héritage** d’élément dans le **boîte à outils** et relâchez le bouton de la souris, cliquez sur la deuxième copie de la classe que vous avez créé à l’étape 3, puis cliquez sur la première classe que vous avez créé à l’étape 2. La flèche sur la ligne d'héritage pointe sur la première classe.  
  
5.  Dans chaque classe, supprimez toutes les propriétés d'objet que vous ne souhaitez pas voir apparaître et qui ne sont pas utilisées pour des associations. Vous recevrez une erreur si vous tentez de supprimer des propriétés de l’objet utilisées pour les associations : [la propriété \<nom de propriété > ne peut pas être supprimé, car il participe à l’association \<nom de l’association >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Comme une classe dérivée hérite des propriétés définies dans sa classe de base, les mêmes colonnes ne peuvent pas être définies dans chaque classe. (Les colonnes sont implémentées sous forme de propriétés.) Vous pouvez activer la création de colonnes dans la classe dérivée en définissant le Modificateur d'héritage sur la propriété dans la classe de base. Pour plus d’informations, consultez [NOT IN BUILD : substitution de propriétés et méthodes](http://msdn.microsoft.com/en-us/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  Sélectionnez la ligne d'héritage dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
7.  Dans le **propriétés** fenêtre, définissez la **propriété de discriminateur** au nom de colonne qui est utilisé pour distinguer les enregistrements dans vos classes.  
  
8.  Définir le **valeur de discriminateur de classe dérivée** valeur à la propriété dans la base de données qui désigne l’enregistrement comme type hérité. (Il s'agit de la valeur stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe héritée.)  
  
9. Définir le **valeur de discriminateur de classe de Base** valeur à la propriété qui désigne l’enregistrement comme type de base. (Il s'agit de la valeur stockée dans la colonne de discriminateur et qui est utilisée pour désigner la classe de base.)  
  
10. Si vous le souhaitez, vous pouvez également définir le **héritage par défaut** propriété pour désigner un type dans une hiérarchie d’héritage qui est utilisé lors du chargement de lignes ne correspondant pas à un de défini le code d’héritage. En d’autres termes, si un enregistrement a une valeur dans la colonne de discriminateur qui ne correspond pas la valeur de la **valeur de discriminateur de classe dérivée** ou **valeur de discriminateur de classe de Base** propriétés, l’enregistrement se charge selon le type désigné comme le **héritage par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [PAVE quelles sont les nouveautés pour le développement d’applications de données dans Visual Studio 2012](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Procédure pas à pas : Création des Classes LINQ to SQL à l’aide d’héritage à Table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NOT IN BUILD : Héritage en Visual Basic](http://msdn.microsoft.com/en-us/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Héritage](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)

