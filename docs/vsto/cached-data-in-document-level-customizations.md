---
title: "Mise en cache des données dans les personnalisations au niveau du Document | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f90aeb03dd62d76064124e9870a5a4dbcd250621
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="cached-data-in-document-level-customizations"></a>Données mises en cache dans des personnalisations au niveau du document
  Des objectifs principaux des personnalisations au niveau du document sont à séparer les données de la vue dans des documents Office. Les données font référence aux informations stockées dans le document, y compris des nombres et du texte. Vue fait référence à l’interface utilisateur et le modèle objet de Microsoft Office Word et Microsoft Office Excel.  
  
 Visual Studio sépare les données de la vue dans les personnalisations au niveau du document en permettant aux données d’être incorporées comme un *îlot de données*, également appelé le *cache de données*. Vous pouvez lire ou modifier les données directement sans démarrer Word ou Excel. Cela est utile lorsque vous avez besoin modifier les données dans des documents sur un serveur qui n’a pas de Microsoft Office est installé. Word et Excel sont destinées à utiliser dans les environnements clients ; ils ne sont pas conçus pour être exécuté sur un serveur.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Pour plus d’informations sur les personnalisations au niveau du document, consultez [présentation du développement de Solutions Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) et [Architecture des personnalisations au niveau du Document](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understanding-the-cached-data-programming-model"></a>Présentation du modèle de programmation de données mises en cache  
 L’îlot de données peut contenir n’importe quel objet dans votre solution qui répond à certaines exigences. Ces objets incluent <xref:System.Data.DataSet> objets, <xref:System.Data.DataTable> objets et tout autre objet qui peut être sérialisé par la <xref:System.Xml.Serialization.XmlSerializer> classe. Pour plus d’informations, consultez [mise en cache des données](../vsto/caching-data.md).  
  
 Pour consulter les données mises en cache, vous pouvez lier des contrôles Windows Forms et *contrôles hôtes* sur le document à des objets dans l’îlot de données. Liaison de données entre l’îlot de données et les contrôles liés aux données conserve les deux synchronisés. Vous pouvez également ajouter le code de validation pour les données qui est indépendantes des contrôles. Pour plus d’informations, consultez [liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Contrôles hôtes sont étendus des versions des objets natifs dans les modèles objet Excel et Word. Contrairement aux objets natifs, les contrôles hôtes peuvent être liés directement aux objets de données managées. Pour plus d’informations, consultez [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) et [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="accessing-cached-data-on-the-server"></a>L’accès aux données mises en cache sur le serveur  
 Pour accéder aux données mises en cache dans un document, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Cette classe fait partie de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], et il peut être utilisé sur un serveur sans exécuter Excel ou Word. Lorsque l’utilisateur ouvre le document une fois que vous modifiez les données mises en cache, tous les contrôles qui sont liés aux données sont automatiquement synchronisés avec les modifications et l’utilisateur est présenté avec les données mises à jour. Pour plus d'informations, consultez [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel et Word ne sont pas nécessaires pour écrire dans les données sur le serveur, uniquement pour les afficher sur le client. Excel et Word est même inutile être installé sur le serveur. Cela fournit une plus grande évolutivité et la possibilité d’effectuer un traitement rapide de lots de documents qui contiennent des îlots de données.  
  
## <a name="data-caching-for-offline-use"></a>La mise en cache pour une utilisation hors connexion de données  
 Le stockage des données dans l’îlot de données permet des scénarios hors connexion. Lorsqu’un utilisateur ouvre un document tout d’abord ou demande le document à partir du serveur, l’îlot de données est remplie avec les données les plus récentes. L’îlot de données est mis en cache dans le document et est ensuite disponible en mode hors connexion. L’utilisateur (et votre code) peuvent manipuler les données, même si aucune connexion active n’est disponible. Lorsque l’utilisateur se reconnecte, les modifications apportées aux données peuvent être propagées à la source de données de serveur.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Données mises en cache et comparées des parties XML personnalisées  
 Parties XML personnalisées ont été introduites dans Microsoft Office system 2007 comme un moyen de stocker des fragments XML arbitraires dans un document. Bien que des parties XML personnalisées sont utiles dans de nombreux scénarios d’identiques en tant que le cache de données, il existe quelques différences entre l’îlot de données et les parties XML personnalisées. Pour plus d’informations sur les parties XML personnalisées, consultez [une vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).  
  
 Le tableau suivant répertorie certaines des différences et similitudes.  
  
||Cache de données|Parties XML personnalisées|  
|-|----------------|----------------------|  
|Les applications Office peuvent les utiliser ?|Personnalisations au niveau du document pour les applications suivantes :<br /><br /> -Excel<br />-Word|Solutions au niveau du document et de niveau application pour les applications suivantes :<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|Les types de données peut stocker ?|Tout objet public de votre assembly de personnalisation qui répond à certaines exigences. Pour plus d'informations, consultez [Caching Data](../vsto/caching-data.md).|Toutes les données XML.|  
|Vous accédez aux données sans démarrer des applications Microsoft Office ?|Oui, à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fournie par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Oui, à l’aide de classes dans le <xref:System.IO.Packaging> espace de noms, ou à l’aide du SDK de Format Open XML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Données dans les Solutions Office](../vsto/data-in-office-solutions.md)   
 [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  