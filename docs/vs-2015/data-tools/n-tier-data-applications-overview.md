---
title: Vue d’ensemble des Applications de données multicouches | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc6bc7e6e7d11b1b5b77cd90b86a6a6167702872
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559887"
---
# <a name="n-tier-data-applications-overview"></a>Vue d'ensemble des applications de données multicouches
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-* de couche données qui sont des données applications sont divisées en plusieurs *niveaux*. Également appelées « applications distribuées » et « applications à plusieurs niveaux », avec applications multicouches séparent le traitement en couches discrètes qui sont distribuées entre le client et le serveur. Lorsque vous développez des applications qui accèdent aux données, vous devez avoir une séparation claire entre les différentes couches qui composent l’application.  
  
 Une application multiniveaux classique inclut une couche Présentation, une couche intermédiaire et une couche Données. Pour séparer plusieurs couches dans une application multicouche, la plus simple consiste à créer des projets distincts pour chaque niveau que vous souhaitez inclure dans votre application. Par exemple, la couche de présentation peut être une application Windows Forms, tandis que la logique d’accès aux données peut être une bibliothèque de classes située dans la couche intermédiaire. En outre, la couche de présentation peut communiquer avec la logique d’accès aux données dans la couche intermédiaire via un service tel qu’un service. La séparation des composants d'application en couches distinctes renforce la facilité de maintenance et l'évolutivité de l'application. Pour cela, l’activation facilitant l’adoption de nouvelles technologies qui peuvent être appliqués à une couche unique sans avoir à reconcevoir toute la solution. En outre, avec applications multicouches stockent généralement les informations sensibles dans la couche intermédiaire, ce qui assure l’isolation de la couche de présentation.  
  
 Visual Studio contient plusieurs fonctionnalités pour aider les développeurs à créer des applications à plusieurs niveaux :  
  
- Le Concepteur de DataSet fournit un **DataSet Project** propriété qui vous permet de séparer le jeu de données (couche d’entité de données) et `TableAdapter`s (couche d’accès aux données) dans des projets distincts.  
  
- Le [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fournit des paramètres pour générer les classes DataContext et les données dans les espaces de noms distincts. Cela permet une séparation logique de l’accès aux données et couches d’entité de données.  
  
- [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) fournit le <xref:System.Data.Linq.Table%601.Attach%2A> méthode qui vous permet de rassembler le DataContext de différentes couches dans une application. Pour plus d’informations, consultez [multicouches et des Applications distantes avec LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598).  
  
## <a name="presentation-tier"></a>Couche de présentation  
 Le *couche présentation* est le niveau dans lequel les utilisateurs interagissent avec une application. Il contient souvent une logique d’application supplémentaires également. Composants de la couche présentation standard sont les suivantes :  
  
- Données de liaison des composants, tels que le <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator>.  
  
- Objet de représentations de données, tel que [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) des classes d’entité pour une utilisation dans la couche de présentation.  
  
  La couche de présentation accède généralement à la couche intermédiaire à l’aide d’une référence de service (par exemple, un [Services Windows Communication Foundation et WCF Data Services dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) application). La couche de présentation n’accède pas directement à la couche données. La couche de présentation communique avec la couche de données par le biais du composant d’accès aux données dans la couche intermédiaire.  
  
## <a name="middle-tier"></a>Couche intermédiaire  
 Le *intermédiaire* est la couche de la couche de présentation et de données utilisent pour communiquer avec eux. Composants de niveau intermédiaire standard sont les suivants :  
  
- Logique métier, telles que la validation de données et des règles métier.  
  
- Composants d’accès aux données et logique, telle que la suivante :  
  
  - [Les TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) et [DataAdapters et DataReaders](http://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).  
  
  - Objet de représentations de données, tel que [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) classes d’entité.  
  
  - Services d’application courantes, telles que l’authentification, autorisation et la personnalisation.  
  
  L’illustration suivante montre les fonctionnalités et technologies qui sont disponibles dans Visual Studio et où ils peuvent être intégrées dans la couche intermédiaire d’une application multiniveau.  
  
  ![Intermédiaire des composants de la couche](../data-tools/media/ntiermid.png "NtierMid")  
  Couche intermédiaire  
  
  En règle générale, la couche intermédiaire se connecte à la couche données à l’aide d’une connexion de données. Cette connexion de données est généralement stockée dans le composant d’accès aux données.  
  
## <a name="data-tier"></a>Couche Données  
 Le *couche données* est fondamentalement le serveur qui stocke les données d’une application (par exemple, un serveur exécutant [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).  
  
 L’illustration suivante montre les fonctionnalités et technologies qui sont disponibles dans Visual Studio et où ils peuvent être intégrées dans la couche données d’une application multiniveau.  
  
 ![Composants de couche données](../data-tools/media/ntierdatatier.png "ntierdatatier")  
Couche Données  
  
 La couche données n’est pas accessible directement depuis le client dans la couche de présentation. Au lieu de cela, le composant d’accès aux données dans la couche intermédiaire est utilisé pour la communication entre la présentation et les couches de données.  
  
## <a name="help-for-n-tier-development"></a>Aide pour le développement d’applications multicouches  
 Les rubriques suivantes fournissent des informations sur l’utilisation des applications multicouches :  
  
 [Guide pratique pour séparer les datasets et les TableAdapters en différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
 [Procédure pas à pas : Création d’une application de données multiniveaux](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
  
 [Procédure pas à pas : Ajout d’une Validation à une Application de données multicouches](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
  
 [Applications multicouches et distantes avec LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.Linq.ITable.Attach%2A>   
 [Procédure pas à pas : Création d’une Application de données multicouches](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)   
 [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
