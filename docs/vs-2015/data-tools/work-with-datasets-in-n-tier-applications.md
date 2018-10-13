---
title: Travailler avec des jeux de données dans les applications multiniveau | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d05204edfd7c3cd5daecad3a1cb21ba5ba7e60d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205970"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Utilisation de datasets dans des applications multiniveaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Applications de données multicouches * sont des applications centrées sur les données sont divisées en plusieurs couches logiques (ou *niveaux*). En d'autres termes, une application de données multicouche est une application divisée en plusieurs projets, avec une couche d'accès aux données, une couche de logique métier et une couche Présentation dans son propre projet. Pour plus d’informations, consultez [vue d’ensemble des Applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).  
  
 Les datasets typés ont été améliorés de sorte que les TableAdapters et les classes DataSet puissent être générés dans des projets distincts. Cela permet de rapidement séparer les couches de l'application et de générer des applications de données multicouches.  
  
 Prise en charge des applications multicouches dans les datasets typés permet le développement itératif de l’architecture d’application vers une conception à n niveaux. Elle supprime également la nécessité de séparer manuellement le code dans plusieurs projets. Commencez par concevoir la couche de données à l’aide de la [création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md). Lorsque vous êtes prêt à l’architecture d’application à une conception multicouche, définissez le **DataSet Project** propriété d’un dataset pour générer la classe de jeu de données dans un projet distinct.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour séparer les datasets et les TableAdapters en différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Décrit comment déplacer la classe DataSet générée du projet qui contient les classes TableAdapter générées dans un nouveau projet.  
  
 [Guide pratique pour ajouter du code aux TableAdapters dans des applications multiniveaux](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Décrit comment générer une classe partielle dans laquelle le code peut être ajouté pour un TableAdapter multicouche.  
  
 [Guide pratique pour ajouter du code à des datasets dans des applications multiniveaux](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Décrit comment générer une classe partielle dans laquelle le code peut être ajouté pour un dataset multicouche.  
  
 [Guide pratique pour ajouter la validation à un dataset multiniveau](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Décrit où ajouter le code pour effectuer une validation pendant la modification des données.  
  
 [Procédure pas à pas : création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Fournit des instructions pas à pas pour créer un dataset typé et diviser le code du TableAdapter et du dataset en plusieurs projets.  
  
 [Procédure pas à pas : Ajout d’une Validation à une Application de données multicouches](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Fournit des instructions détaillées pour ajouter une validation à l’application qui a été créée dans la procédure d’application de données multicouche.  
  
## <a name="reference"></a>Référence  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)  
  
 [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)  
  
 [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)  
  
 [Applications multicouches et distantes avec LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

