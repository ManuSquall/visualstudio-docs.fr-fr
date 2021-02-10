---
title: Données mises en cache dans les personnalisations au niveau du document
description: Découvrez comment Visual Studio sépare les données de la vue dans les personnalisations au niveau du document en permettant aux données d’être incorporées en tant que cache de données.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f1c383b5367b2966b9fd082b2d47570264b4d191
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955773"
---
# <a name="cached-data-in-document-level-customizations"></a>Données mises en cache dans les personnalisations au niveau du document
  L’objectif principal des personnalisations au niveau du document est de séparer les données de la vue dans les documents Office. Les données font référence aux informations stockées dans le document, y compris les nombres et le texte. La vue fait référence à l’interface utilisateur et au modèle objet de Microsoft Office Word et Microsoft Office Excel.

 Visual Studio sépare les données de la vue dans les personnalisations au niveau du document en permettant aux données d’être incorporées en tant qu' *îlot de données*, également appelé *cache de données*. Vous pouvez lire ou modifier les données directement sans démarrer Word ou Excel. Cela est utile lorsque vous devez modifier des données dans des documents sur un serveur sur lequel Microsoft Office n’est pas installé. Word et Excel sont destinés à être utilisés dans les environnements clients. elles ne sont pas conçues pour être exécutées sur un serveur.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Pour plus d’informations sur les personnalisations au niveau du document, consultez [vue d’ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) et [architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Comprendre le modèle de programmation de données mis en cache
 L’îlot de données peut contenir n’importe quel objet de votre solution qui répond à certaines exigences. Ces objets incluent <xref:System.Data.DataSet> des objets, des <xref:System.Data.DataTable> objets et tout autre objet qui peut être sérialisé par la <xref:System.Xml.Serialization.XmlSerializer> classe. Pour plus d’informations, consultez mettre [en cache les données](../vsto/caching-data.md).

 Pour fournir la vue des données mises en cache, vous pouvez lier Windows Forms contrôles et les *contrôles hôtes* sur le document aux objets de l’îlot de données. La liaison de données entre l’îlot de données et les contrôles liés aux données conserve les deux synchronisés. Vous pouvez également ajouter du code de validation aux données qui sont indépendantes des contrôles. Pour plus d’informations, consultez [lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Les contrôles hôtes sont des versions étendues d’objets natifs dans les modèles objet Excel et Word. Contrairement aux objets natifs, les contrôles hôtes peuvent être liés directement aux objets de données managées. Pour plus d’informations, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md) et [Windows Forms contrôles sur les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Accéder aux données mises en cache sur le serveur
 Pour accéder aux données mises en cache dans un document, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Cette classe fait partie de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , et elle peut être utilisée sur un serveur sans exécuter Excel ou Word. Lorsque l’utilisateur ouvre le document après avoir modifié les données mises en cache, tous les contrôles liés aux données sont automatiquement synchronisés avec les modifications, et l’utilisateur reçoit les données mises à jour. Pour plus d’informations, consultez [accéder aux données dans les documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).

 Excel et Word ne sont pas nécessaires pour écrire des données sur le serveur, mais uniquement pour les afficher sur le client. Excel et Word n’ont même pas besoin d’être installés sur le serveur. Cela améliore l’évolutivité et la possibilité d’effectuer un traitement par lots rapide des documents qui contiennent des îlots de données.

## <a name="data-caching-for-offline-use"></a>Mise en cache des données pour une utilisation hors connexion
 Le stockage de données dans l’îlot de données permet des scénarios hors connexion. Lorsqu’un utilisateur ouvre un document ou demande le document à partir du serveur pour la première fois, l’îlot de données est rempli avec les données les plus récentes. L’îlot de données est mis en cache dans le document et est ensuite disponible hors connexion. L’utilisateur (et votre code) peut manipuler les données, même si aucune connexion active n’est disponible. Lorsque l’utilisateur se reconnecte, les modifications apportées aux données peuvent être propagées vers une source de données serveur.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Comparaison des données mises en cache et des parties XML personnalisées
 Les parties XML personnalisées ont été introduites dans le système 2007 Microsoft Office pour stocker des éléments de code XML arbitraires dans un document. Bien que les parties XML personnalisées soient utiles dans de nombreux scénarios identiques à ceux du cache de données, il existe des différences entre l’îlot de données et les parties XML personnalisées. Pour plus d’informations sur les parties XML personnalisées, consultez [vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).

 Le tableau suivant répertorie certaines des différences et similarités.

|Question/caractéristique|Cache de données|Parties XML personnalisées|
|-|----------------|----------------------|
|Quelles applications Office peuvent utiliser ?|Personnalisations au niveau du document pour les applications suivantes :<br /><br /> -Excel<br />-Word|Solutions au niveau du document et au niveau de l’application pour les applications suivantes :<br /><br /> -Excel<br />-PowerPoint<br />-Word|
|Quels types de données pouvez-vous stocker ?|Tout objet public de votre assembly de personnalisation qui répond à certaines exigences. Pour plus d’informations, consultez mettre [en cache les données](../vsto/caching-data.md).|Toutes les données XML.|
|Pouvez-vous accéder aux données sans démarrer les applications Microsoft Office ?|Oui, à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fournie par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Oui, en utilisant des classes dans l' <xref:System.IO.Packaging> espace de noms, ou en utilisant le kit de développement logiciel (SDK) Open XML format.|

## <a name="see-also"></a>Voir aussi
- [Données dans les solutions Office](../vsto/data-in-office-solutions.md)
- [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
