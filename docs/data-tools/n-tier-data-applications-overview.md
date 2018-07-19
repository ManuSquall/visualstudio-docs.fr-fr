---
title: Vue d'ensemble des applications de données multicouches
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4e386c052b43ee62ddde0516fa203298fe1babe5
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089028"
---
# <a name="n-tier-data-applications-overview"></a>Vue d’ensemble des applications de données multicouches
*Applications multicouches* des applications de données sont des applications de données qui sont séparées en plusieurs *niveaux*. Également appelées « applications distribuées » et « applications à plusieurs niveaux », avec applications multicouches séparent le traitement en couches discrètes qui sont distribuées entre le client et le serveur. Lorsque vous développez des applications qui accèdent aux données, vous devez avoir une séparation claire entre les différentes couches qui composent l’application.

Une application multicouche classique inclut une couche présentation, une couche intermédiaire et une couche de données. Pour séparer plusieurs couches dans une application multicouche, la plus simple consiste à créer des projets distincts pour chaque niveau que vous souhaitez inclure dans votre application. Par exemple, la couche de présentation peut être une application Windows Forms, tandis que la logique d’accès aux données peut être une bibliothèque de classes située dans la couche intermédiaire. En outre, la couche de présentation peut communiquer avec la logique d’accès aux données dans la couche intermédiaire via un service tel qu’un service. La séparation des composants d'application en couches distinctes renforce la facilité de maintenance et l'évolutivité de l'application. Pour cela, l’activation facilitant l’adoption de nouvelles technologies qui peuvent être appliqués à une couche unique sans avoir à reconcevoir toute la solution. En outre, avec applications multicouches stockent généralement les informations sensibles dans la couche intermédiaire, ce qui assure l’isolation de la couche de présentation.

Visual Studio contient plusieurs fonctionnalités pour aider les développeurs à créer des applications à plusieurs niveaux :

-   Le jeu de données fournit un **DataSet Project** propriété qui vous permet de séparer le jeu de données (couche d’entité de données) et les TableAdapters (couche d’accès aux données) dans des projets distincts.

-   Le [des outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit des paramètres pour générer les classes DataContext et les données dans les espaces de noms distincts. Cela permet une séparation logique de l’accès aux données et couches d’entité de données.

-   [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) fournit le <xref:System.Data.Linq.Table%601.Attach%2A> méthode qui vous permet de rassembler le DataContext de différentes couches dans une application. Pour plus d’informations, consultez [multicouches et des applications distantes avec LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Couche de présentation
Le *couche présentation* est le niveau dans lequel les utilisateurs interagissent avec une application. Il contient souvent une logique d’application supplémentaires également. Composants de la couche présentation standard sont les suivantes :

-   Données de liaison des composants, tels que le <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator>.

-   Objet de représentations de données, tel que [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) des classes d’entité pour une utilisation dans la couche de présentation.

La couche de présentation accède généralement à la couche intermédiaire à l’aide d’une référence de service (par exemple, un [Services Windows Communication Foundation et WCF Data Services dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) application). La couche de présentation n’accède pas directement à la couche données. La couche de présentation communique avec la couche de données par le biais du composant d’accès aux données dans la couche intermédiaire.

## <a name="middle-tier"></a>Niveau intermédiaire
Le *intermédiaire* est la couche de la couche de présentation et de données utilisent pour communiquer avec eux. Composants de niveau intermédiaire standard sont les suivants :

-   Logique métier, telles que la validation de données et des règles métier.

-   Composants d’accès aux données et logique, telle que la suivante :

    -   [Les TableAdapters](create-and-configure-tableadapters.md) et [DataAdapters et DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

    -   Objet de représentations de données, tel que [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classes d’entité.

    -   Services d’application courantes, telles que l’authentification, autorisation et la personnalisation.

L’illustration suivante montre les fonctionnalités et technologies qui sont disponibles dans Visual Studio et où ils peuvent être intégrées dans la couche intermédiaire d’une application multiniveau.

![Intermédiaire des composants de la couche](../data-tools/media/ntiermid.png) le niveau intermédiaire

En règle générale, la couche intermédiaire se connecte à la couche données à l’aide d’une connexion de données. Cette connexion de données est généralement stockée dans le composant d’accès aux données.

## <a name="data-tier"></a>Couche Données
Le *couche données* est fondamentalement le serveur qui stocke les données d’une application (par exemple, un serveur exécutant [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]).

L’illustration suivante montre les fonctionnalités et technologies qui sont disponibles dans Visual Studio et où ils peuvent être intégrées dans la couche données d’une application multiniveau.

![Composants de couche données](../data-tools/media/ntierdatatier.png) couche données

La couche données n’est pas accessible directement depuis le client dans la couche de présentation. Au lieu de cela, le composant d’accès aux données dans la couche intermédiaire est utilisé pour la communication entre la présentation et les couches de données.

## <a name="help-for-n-tier-development"></a>Aide pour le développement d’applications multicouches
Les rubriques suivantes fournissent des informations sur l’utilisation des applications multicouches :

[Guide pratique pour séparer les datasets et les TableAdapters en différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Procédure pas à pas : Création d’une application de données multicouches](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[Applications multicouches et des applications distantes avec LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Création d’une application de données multicouches](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)