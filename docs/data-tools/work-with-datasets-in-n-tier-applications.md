---
title: Utilisation de datasets dans des applications multiniveaux
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c6da3f51a249aaf52cf3f20b90f3add6ceeb7aa1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936549"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Utilisation de datasets dans des applications multiniveaux

Les *applications de données multiniveaux* sont des applications centrées sur les données divisées en plusieurs *couches* logiques. En d'autres termes, une application de données multicouche est une application divisée en plusieurs projets, avec une couche d'accès aux données, une couche de logique métier et une couche Présentation dans son propre projet. Pour plus d’informations, consultez [vue d’ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).

Les datasets typés ont été améliorés de sorte que les TableAdapters et les classes DataSet puissent être générés dans des projets distincts. Cela permet de rapidement séparer les couches de l'application et de générer des applications de données multicouches.

Prise en charge des applications multicouches dans les datasets typés permet le développement itératif de l’architecture d’application vers une conception à n niveaux. Elle supprime également la nécessité de séparer manuellement le code dans plusieurs projets. Commencez par concevoir la couche de données à l’aide de la **Concepteur de Dataset**. Quand vous êtes prêt à faire évoluer l’architecture de l’application vers une conception multiniveaux, définissez la propriété **DataSet Project** d’un dataset pour qu’elle génère la classe DataSet dans un projet distinct.

## <a name="reference"></a>Référence

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)
- [Procédure pas à pas : Création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Guide pratique pour ajouter du code aux TableAdapters dans des applications multiniveaux](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Guide pratique pour ajouter du code à des datasets dans des applications multiniveaux](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Guide pratique pour ajouter la validation à un dataset multiniveau](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Guide pratique pour séparer les datasets et les TableAdapters en différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)
- [Applications multicouches et distantes avec LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)