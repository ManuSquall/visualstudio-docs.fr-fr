---
title: 'Procédure pas à pas : Exemple LinqToXmlDataBinding | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 379c95e4de7831c833d8d82d48643a9da10be323
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187479"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Procédure pas à pas : Exemple LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas décrit l'exemple LinqToXmlDataBinding et fournit des explications concernant les aspects les plus intéressants du contenu des deux principaux fichiers sources, L2DBForm.xaml et L2DBForm.xaml.cs.  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de lire cette procédure pas à pas, nous vous conseillons vivement de générer et d’exécuter le programme LinqToXmlDataBinding décrit dans [Guide pratique pour Générer et exécuter l’exemple LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).  
  
## <a name="remarks"></a>Notes  
 Le programme LinqToXmlDataBinding est une application WPF (Windows Presentation Foundation) composée de fichiers sources C# et XAML. Il contient un document XML incorporé qui définit une liste de livres et permet à l'utilisateur d'afficher, d'ajouter, de supprimer et de modifier ces entrées. Il est constitué des deux principaux fichiers sources suivants :  
  
- L2DBForm.xaml contient le code de déclaration XAML pour l'interface utilisateur de la fenêtre principale. Il contient également une section de ressources de fenêtre qui définit un fournisseur de données et un document XML incorporé pour les listes de livres.  
  
- L2DBForm.xaml.cs contient les méthodes d'initialisation et de gestion d'événements associées à l'interface utilisateur.  
  
  La fenêtre principale est composée des quatre sections d'interface utilisateur verticales suivantes :  
  
- **XML** affiche la source XML brute de la liste de livres incorporée.  
  
- **Book List** affiche les entrées de livres au format texte standard et permet à l’utilisateur de sélectionner et de supprimer des entrées.  
  
- **Edit Selected Book** permet à l’utilisateur de modifier les valeurs associées à l’entrée de livre sélectionnée.  
  
- **Add New Book** permet la création d’une nouvelle entrée de livre sur la base des valeurs entrées par l’utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Code source L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Présente le contenu et la description du code XAML dans le fichier L2DBForm.xaml.|  
|[Code source L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Présente le contenu et la description du code source C# dans le fichier L2DBForm.xaml.cs.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de liaison de données WPF à l’aide de LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Guide pratique : générer et exécuter l’exemple LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)
