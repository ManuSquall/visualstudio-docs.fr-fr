---
title: Utilisation de datasets dans des applications multiniveaux
description: Apprenez à utiliser des jeux de données dans des applications multicouches. Les applications de données multicouches sont des applications centrées sur les données qui sont divisées en plusieurs couches logiques (ou niveaux).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d450bb60bdb604f658f73d0b5df4b9bd739cf923
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998185"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Utilisation de datasets dans des applications multiniveaux

Les *applications de données multicouches* sont des applications centrées sur les données qui sont divisées en plusieurs couches logiques (ou *niveaux*). En d'autres termes, une application de données multicouche est une application divisée en plusieurs projets, avec une couche d'accès aux données, une couche de logique métier et une couche Présentation dans son propre projet. Pour plus d’informations, consultez [vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).

Les datasets typés ont été améliorés de sorte que les TableAdapters et les classes DataSet puissent être générés dans des projets distincts. Cela permet de rapidement séparer les couches de l'application et de générer des applications de données multicouches.

La prise en charge multiniveau dans les jeux de données typés permet le développement itératif de l’architecture de l’application vers une conception multicouche. Elle supprime également la nécessité de séparer manuellement le code en plusieurs projets. Commencez à concevoir la couche de données à l’aide de l' **Concepteur de DataSet**. Quand vous êtes prêt à faire évoluer l’architecture de l’application vers une conception multiniveaux, définissez la propriété **DataSet Project** d’un dataset pour qu’elle génère la classe DataSet dans un projet distinct.

## <a name="reference"></a>Informations de référence

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)
- [Procédure pas à pas : création d’une application de données multicouches](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Ajouter du code aux TableAdapters dans des applications multiniveaux](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Ajouter du code à des datasets dans des applications multiniveaux](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Ajouter la validation à un dataset multiniveau](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Séparer les datasets et les TableAdapters en différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)
- [Applications multicouches et distantes avec LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
