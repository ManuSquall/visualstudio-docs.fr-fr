---
title: Données mises en cache dans les personnalisations au niveau du document
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74a6c196bbde0ae6765627e768dd926b992d374d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868272"
---
# <a name="cached-data-in-document-level-customizations"></a>Données mises en cache dans les personnalisations au niveau du document
  Des principaux objectifs des personnalisations au niveau du document sont de séparer les données à partir de la vue dans les documents Office. Les données font référence aux informations stockées dans le document, y compris des nombres et du texte. Vue fait référence à l’interface utilisateur et le modèle objet de Microsoft Office Word et Microsoft Office Excel.  
  
 Visual Studio sépare les données de la vue dans les personnalisations au niveau du document en permettant aux données d’être incorporées comme un *îlot de données*, également appelé le *cache de données*. Vous pouvez lire ou modifier les données directement sans démarrer Word ou Excel. Cela est utile lorsque vous avez besoin modifier des données dans des documents sur un serveur qui n’a pas de Microsoft Office est installé. Word et Excel sont destinées à utiliser dans des environnements clients ; elles ne sont pas conçues pour être exécuté sur un serveur.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Pour plus d’informations sur les personnalisations au niveau du document, consultez [présentation du développement de solutions Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) et [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Comprendre le modèle de programmation de données mises en cache  
 L’îlot de données peut contenir n’importe quel objet dans votre solution qui répond à certaines exigences. Ces objets incluent <xref:System.Data.DataSet> objets, <xref:System.Data.DataTable> objets et tout autre objet qui peut être sérialisé par la <xref:System.Xml.Serialization.XmlSerializer> classe. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).  
  
 Pour consulter les données mises en cache, vous pouvez lier des contrôles Windows Forms et *contrôles hôtes* sur le document à des objets dans l’îlot de données. Liaison de données entre l’îlot de données et les contrôles liés aux données conserve les deux synchronisés. Vous pouvez également ajouter le code de validation aux données qui est indépendantes des contrôles. Pour plus d’informations, consultez [lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Contrôles hôtes sont étendus des versions d’objets natifs dans les modèles objet Excel et Word. Contrairement aux objets natifs, contrôles hôtes peuvent être liés directement aux objets de données managées. Pour plus d’informations, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md) et [des contrôles de Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Accès mis en cache les données sur le serveur  
 Pour accéder aux données mises en cache dans un document, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Cette classe fait partie de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], et il peut être utilisé sur un serveur sans exécuter Excel ou Word. Lorsque l’utilisateur ouvre le document une fois que vous modifiez les données mises en cache, tous les contrôles qui sont liés aux données sont automatiquement synchronisés avec les modifications, et l’utilisateur est présenté avec les données mises à jour. Pour plus d’informations, consultez [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel et Word ne sont pas nécessaires pour écrire dans les données sur le serveur, uniquement pour l’afficher sur le client. Excel et Word est même inutile être installé sur le serveur. Cela fournit une plus grande évolutivité et la possibilité d’effectuer le traitement rapide de lots de documents qui contiennent des îlots de données.  
  
## <a name="data-caching-for-offline-use"></a>La mise en cache pour une utilisation hors connexion de données  
 Stockage des données dans l’îlot de données permet des scénarios hors connexion. Lorsqu’un utilisateur ouvre un document tout d’abord ou demande le document à partir du serveur, l’îlot de données est remplie avec les données les plus récentes. L’îlot de données est mis en cache dans le document, puis est disponible hors connexion. L’utilisateur (et votre code) peuvent manipuler les données, même si aucune connexion active n’est disponible. Lorsque l’utilisateur se reconnecte, les modifications apportées aux données peuvent être propagées à la source de données de serveur.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Données mises en cache et les parties XML personnalisées par rapport  
 Parties XML personnalisées ont été introduits dans Microsoft Office system 2007 comme un moyen de stocker des fragments XML arbitraires dans un document. Bien que les parties XML personnalisées sont utiles dans de nombreux scénarios de cache de données, il existe certaines différences entre l’îlot de données et les parties XML personnalisées. Pour plus d’informations sur les parties XML personnalisées, consultez [vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).  
  
 Le tableau suivant répertorie certaines des différences et similitudes.  
  
||Cache de données|Parties XML personnalisées|  
|-|----------------|----------------------|  
|Les applications Office peuvent les utiliser ?|Personnalisations au niveau du document pour les applications suivantes :<br /><br /> -   Excel<br />-   Word|Solutions au niveau du document et de niveau application pour les applications suivantes :<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|  
|Les types de données peut stocker ?|Tout objet public de votre assembly de personnalisation qui répond à certaines exigences. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).|Toutes les données XML.|  
|Vous accédez aux données sans démarrer des applications Microsoft Office ?|Oui, à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fournie par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Oui, en utilisant des classes dans le <xref:System.IO.Packaging> espace de noms, ou à l’aide du SDK de Format Open XML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Données dans les solutions Office](../vsto/data-in-office-solutions.md)   
 [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
