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
ms.openlocfilehash: 59f273c511a24b1139b03421c2ca59871350aec3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="n-tier-data-applications-overview"></a>Vue d'ensemble des applications de données multicouches
*Multicouches* applications de données sont des applications de données qui sont séparées en plusieurs *niveaux*. Également appelées « applications distribuées » et « applications à plusieurs niveaux », avec applications multicouches séparent le traitement en couches discrètes qui sont distribuées entre le client et le serveur. Lorsque vous développez des applications qui accèdent aux données, vous devez avoir une distinction claire entre les différentes couches qui composent votre application.

Une application multicouche classique inclut une couche présentation, une couche intermédiaire et une couche de données. Pour séparer plusieurs couches dans une application multicouche, la plus simple consiste à créer des projets distincts pour chaque couche que vous souhaitez inclure dans votre application. Par exemple, la couche présentation peut être une application Windows Forms, tandis que la logique d’accès aux données peut-être être une bibliothèque de classes située dans la couche intermédiaire. En outre, la couche de présentation peut communiquer avec la logique d’accès aux données dans la couche intermédiaire via un service tel qu’un service. La séparation des composants d'application en couches distinctes renforce la facilité de maintenance et l'évolutivité de l'application. Pour cela, l’activation facilitant l’adoption de nouvelles technologies qui peuvent être appliquées à une couche unique sans avoir à reconcevoir toute la solution. En outre, les applications multicouches stockent généralement les informations sensibles dans la couche intermédiaire, ce qui assure l’isolation de la couche de présentation.

Visual Studio contient plusieurs fonctionnalités pour aider les développeurs à créer des applications multicouches :

-   Le jeu de données fournit un **projet DataSet** propriété qui vous permet de séparer le jeu de données (couche d’entité de données) et les TableAdapters (couche d’accès aux données) dans des projets distincts.

-   Le [LINQ to SQL Tools dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit des paramètres pour générer les classes DataContext et les données dans les espaces de noms distincts. Cela permet une séparation logique de l’accès aux données et les couches d’entité de données.

-   [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) fournit le <xref:System.Data.Linq.Table%601.Attach%2A> méthode qui vous permet de rassembler le DataContext de différentes couches dans une application. Pour plus d’informations, consultez [multicouches et des Applications distantes avec LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Couche de présentation
Le *couche présentation* correspond à la couche dans laquelle les utilisateurs interagissent avec une application. Il contient souvent une logique d’application supplémentaires également. Composants de la couche présentation standard sont les suivantes :

-   Liaison des composants, tels que des données la <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator>.

-   Objet de représentations de données, tel que [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) des classes d’entité pour une utilisation dans la couche de présentation.

La couche de présentation accède généralement à la couche intermédiaire à l’aide d’une référence de service (par exemple, un [Services Windows Communication Foundation et Services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) application). La couche de présentation n’accède pas directement à la couche données. La couche présentation communique avec la couche données par le biais du composant d’accès aux données dans la couche intermédiaire.

## <a name="middle-tier"></a>Couche intermédiaire
Le *intermédiaire* est la couche de la couche de présentation et de données utilisent pour communiquer entre eux. Les composants de niveau intermédiaire standard sont les suivants :

-   Logique métier, telles que la validation de données et les règles métier.

-   Composants d’accès aux données et la logique, telle que la suivante :

    -   [Les TableAdapters](create-and-configure-tableadapters.md) et [DataAdapters et DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

    -   Objet de représentations de données, tel que [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) des classes d’entité.

    -   Services d’application courants, tels que l’authentification, autorisation et la personnalisation.

L’illustration suivante montre les fonctionnalités et technologies qui sont disponibles dans Visual Studio et où ils peuvent être intégrées dans la couche intermédiaire d’une application multicouche.

![Composants de la couche de milieu](../data-tools/media/ntiermid.png "NtierMid") niveau intermédiaire

En règle générale, la couche intermédiaire se connecte à la couche données à l’aide d’une connexion de données. Cette connexion de données est généralement stockée dans le composant d’accès aux données.

## <a name="data-tier"></a>Couche Données
Le *couche données* est fondamentalement le serveur qui stocke les données d’une application (par exemple, un serveur exécutant [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]).

L’illustration suivante montre les fonctionnalités et technologies qui sont disponibles dans Visual Studio et où ils peuvent être intégrées dans la couche données d’une application multicouche.

![Composants de couche données](../data-tools/media/ntierdatatier.png "ntierdatatier") couche données

La couche données ne sont pas accessibles directement depuis le client dans la couche de présentation. Au lieu de cela, le composant d’accès aux données dans la couche intermédiaire est utilisé pour la communication entre la présentation et les niveaux de données.

## <a name="help-for-n-tier-development"></a>Aide pour le développement de couches
Les rubriques suivantes fournissent des informations sur l’utilisation des applications multicouches :

[Guide pratique pour séparer les datasets et les TableAdapters en différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Procédure pas à pas : création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[Applications multicouches et distantes avec LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)