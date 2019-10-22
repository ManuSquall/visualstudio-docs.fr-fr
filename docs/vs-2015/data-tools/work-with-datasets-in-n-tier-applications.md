---
title: Utiliser des jeux de données dans des applications multicouches | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657813"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Utilisation de datasets dans des applications multiniveaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les applications de données multicouches * sont des applications centrées sur les données qui sont divisées en plusieurs couches logiques (ou *niveaux*). En d'autres termes, une application de données multicouche est une application divisée en plusieurs projets, avec une couche d'accès aux données, une couche de logique métier et une couche Présentation dans son propre projet. Pour plus d’informations, consultez [vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).

 Les datasets typés ont été améliorés de sorte que les TableAdapters et les classes DataSet puissent être générés dans des projets distincts. Cela permet de rapidement séparer les couches de l'application et de générer des applications de données multicouches.

 La prise en charge multiniveau dans les jeux de données typés permet le développement itératif de l’architecture de l’application vers une conception multicouche. Elle supprime également la nécessité de séparer manuellement le code en plusieurs projets. Commencez à concevoir la couche de données à l’aide de l’Concepteur de DataSet. Quand vous êtes prêt à faire évoluer l’architecture de l’application vers une conception multiniveaux, définissez la propriété **DataSet Project** d’un dataset pour qu’elle génère la classe DataSet dans un projet distinct.

## <a name="in-this-section"></a>Dans cette section
 [Séparer des DataSets et des TableAdapters dans différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Décrit comment déplacer la classe DataSet générée à partir du projet qui contient les classes TableAdapter générées et dans un nouveau projet.

 [Ajouter du code aux TableAdapters dans des applications multicouches](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Décrit comment générer une classe partielle dans laquelle le code peut être ajouté pour un TableAdapter à n niveaux.

 [Ajouter du code à des jeux de données dans des applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md) Décrit comment générer une classe partielle dans laquelle le code peut être ajouté pour un DataSet multicouche.

 [Ajouter la validation à un DataSet multicouche](../data-tools/add-validation-to-an-n-tier-dataset.md) Explique où ajouter du code pour effectuer une validation sur les modifications de données.

 [Procédure pas à pas : création d’une application de données multicouches](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Fournit des instructions pas à pas pour la création d’un DataSet typé et la séparation du code du TableAdapter et du DataSet dans plusieurs projets.

 [Procédure pas à pas : ajout d’une validation à une application de données multicouche](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) Fournit des instructions pas à pas pour ajouter une validation à l’application créée dans la procédure pas à pas de l’application de données multicouches.

## <a name="reference"></a>Reference
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>Rubriques connexes

- [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Applications multicouches et distantes avec LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)