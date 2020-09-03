---
title: Vue d’ensemble des applications de données multicouches | Microsoft Docs
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
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f124e997669370e71819cf37423d0c2d6a414d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658053"
---
# <a name="n-tier-data-applications-overview"></a>Vue d'ensemble des applications de données multicouches
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les applications de données multicouches * sont des applications de données qui sont séparées en plusieurs *niveaux*. Également appelés « applications distribuées » et « applications multicouches », les applications multicouches séparent le traitement en niveaux discrets répartis entre le client et le serveur. Lorsque vous développez des applications qui accèdent à des données, vous devez disposer d’une séparation claire entre les différents niveaux qui composent l’application.

 Une application multiniveaux classique inclut une couche Présentation, une couche intermédiaire et une couche Données. Le moyen le plus simple de séparer les différents niveaux dans une application multiniveau consiste à créer des projets discrets pour chaque niveau que vous souhaitez inclure dans votre application. Par exemple, la couche de présentation peut être une application Windows Forms, tandis que la logique d’accès aux données peut être une bibliothèque de classes située dans la couche intermédiaire. En outre, la couche de présentation peut communiquer avec la logique d’accès aux données de la couche intermédiaire par le biais d’un service tel qu’un service. La séparation des composants d'application en couches distinctes renforce la facilité de maintenance et l'évolutivité de l'application. Pour ce faire, il facilite l’adoption de nouvelles technologies qui peuvent être appliquées à un seul niveau sans avoir à reconcevoir l’ensemble de la solution. En outre, les applications multicouches stockent généralement des informations sensibles dans la couche intermédiaire, ce qui maintient l’isolation à partir du niveau de présentation.

 Visual Studio contient plusieurs fonctionnalités pour aider les développeurs à créer des applications multicouches :

- Le concepteur de DataSet fournit une propriété de **projet DataSet** qui vous permet de séparer le DataSet (couche d’entité de données) et le `TableAdapter` s (couche d’accès aux données) en projets discrets.

- Les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournissent des paramètres pour générer le DataContext et les classes de données dans des espaces de noms distincts. Cela permet de séparer logiquement les niveaux d’accès aux données et d’entité de données.

- [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) fournit la <xref:System.Data.Linq.Table%601.Attach%2A> méthode qui vous permet de réunir le DataContext de différents niveaux dans une application. Pour plus d’informations, consultez [applications multicouches et distantes avec LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598).

## <a name="presentation-tier"></a>Couche de présentation
 La *couche présentation* est le niveau dans lequel les utilisateurs interagissent avec une application. Elle contient souvent également une logique d’application supplémentaire. Les composants standard de la couche présentation sont les suivants :

- Composants de liaison de données, tels que <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> .

- Représentations d’objets de données, telles que les [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) les classes d’entité à utiliser dans la couche de présentation.

  La couche présentation accède généralement à la couche intermédiaire à l’aide d’une référence de service (par exemple, un [Windows Communication Foundation services et WCF Data Services dans l’application Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ). La couche présentation n’accède pas directement à la couche données. La couche présentation communique avec la couche données par le biais du composant d’accès aux données de la couche intermédiaire.

## <a name="middle-tier"></a>Couche intermédiaire
 La couche *intermédiaire* est la couche que la couche de présentation et la couche de données utilisent pour communiquer entre elles. Les composants de niveau intermédiaire classiques sont les suivants :

- Logique métier, telle que les règles d’entreprise et la validation des données.

- Les composants et la logique d’accès aux données, tels que les suivants :

  - [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) et [DataAdapters et DataReaders](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

  - Représentations d’objets de données, telles que les [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) les classes d’entité.

  - Services d’application courants, tels que l’authentification, l’autorisation et la personnalisation.

  L’illustration suivante montre les fonctionnalités et les technologies qui sont disponibles dans Visual Studio et l’endroit où elles peuvent tenir dans la couche intermédiaire d’une application multiniveau.

  ![Composants de la couche intermédiaire](../data-tools/media/ntiermid.png "NtierMid") Niveau intermédiaire

  En général, la couche intermédiaire se connecte à la couche données à l’aide d’une connexion de données. Cette connexion de données est généralement stockée dans le composant d’accès aux données.

## <a name="data-tier"></a>Couche Données
 La *couche données* est fondamentalement le serveur qui stocke les données d’une application (par exemple, un serveur exécutant [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).

 L’illustration suivante montre les fonctionnalités et les technologies qui sont disponibles dans Visual Studio et l’endroit où elles peuvent être intégrées à la couche données d’une application multiniveau.

 ![Composants de la couche données](../data-tools/media/ntierdatatier.png "ntierdatatier") Couche données

 La couche données n’est pas accessible directement à partir du client dans la couche présentation. Au lieu de cela, le composant d’accès aux données de la couche intermédiaire est utilisé pour la communication entre les couches présentation et données.

## <a name="help-for-n-tier-development"></a>Aide pour le développement multiniveau
 Les rubriques suivantes fournissent des informations sur l’utilisation des applications multicouches :

 [Séparer des DataSets et des TableAdapters dans différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

 [Procédure pas à pas : création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

 [Procédure pas à pas : ajout d'une validation à une application de données multicouche](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)

 [Applications multicouches et distantes avec LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

## <a name="see-also"></a>Voir aussi
 <xref:System.Data.Linq.ITable.Attach%2A>[Procédure pas à pas : création d’une application de données multicouche](../data-tools/walkthrough-creating-an-n-tier-data-application.md) outils de jeu de données de [mise à jour hiérarchique](../data-tools/hierarchical-update.md) [dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
