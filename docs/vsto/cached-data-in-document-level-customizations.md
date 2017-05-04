---
title: "Donn&#233;es mises en cache dans des personnalisations au niveau du document | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "mettre en cache des données (développement Office dans Visual Studio), à propos de la mise en cache de données"
  - "données (développement Office dans Visual Studio), cache"
  - "données (développement Office dans Visual Studio), solutions au niveau du document"
  - "mise en cache de données (développement Office dans Visual Studio), à propos de la mise en cache de données"
  - "îlots de données (développement Office dans Visual Studio)"
  - "personnalisations au niveau du document (développement Office dans Visual Studio), modèle de données"
  - "affichage (développement Office dans Visual Studio)"
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Donn&#233;es mises en cache dans des personnalisations au niveau du document
  L'un des objectifs principaux des personnalisations au niveau du document consiste à scinder les données et leur affichage dans les documents Office.  Par "données", on entend les informations stockées dans le document, dont les nombres et le texte.  Quant à l'affichage, il fait référence à l'interface utilisateur et au modèle objet de Microsoft Office Word et de Microsoft Office Excel.  
  
 Visual Studio sépare les données de la vue dans les personnalisations au niveau du document en permettant aux données d'être incorporées comme un *îlot de données*, également appelé *cache de données*.  Vous pouvez ainsi lire ou modifier directement les données sans démarrer Word ou Excel.  Cette procédure est utile lorsque vous devez modifier des données d'un document sur un serveur qui n'est pas équipé de Microsoft Office.  Word et Excel sont conçus pour être utilisés dans des environnements clients ; ils ne sont pas destinés à être exécutés sur un serveur.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Pour plus d'informations sur les personnalisations au niveau du document, consultez [Vue d'ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) et [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).  
  
## Fonctionnement du modèle de programmation des données en mémoire cache  
 Les îlots de données peuvent contenir tout objet de votre solution répondant à certaines exigences.  Parmi ceux\-ci, citons les objets <xref:System.Data.DataSet>, <xref:System.Data.DataTable> et tout autre objet qui peut être sérialisé par la classe <xref:System.Xml.Serialization.XmlSerializer>.  Pour plus d'informations, consultez [Mise en cache des données](../vsto/caching-data.md).  
  
 Pour consulter les données en mémoire cache, vous pouvez lier des contrôles Windows Forms et *des contrôles hôtes* du document aux objets de l'îlot de données.  La liaison entre l'îlot de données et les contrôles liés aux données veille à ce que les deux restent synchronisés.  Vous pouvez également ajouter aux données un code de validation indépendant des contrôles.  Pour plus d’informations, consultez [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Les contrôles hôtes sont des versions étendues d'objets natifs des modèles objets d'Excel et de Word.  Contrairement aux objets natifs, les contrôles hôtes peuvent être liés directement aux objets de données managées.  Pour plus d'informations, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md) et [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## Accès aux données en mémoire cache sur le serveur  
 Pour accéder aux données en mémoire cache dans un document, vous pouvez utiliser la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  Cette classe fait partie de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] et peut être utilisée sur un serveur sans exécuter Excel ou Word.  Lorsqu'un utilisateur ouvre le document après la modification des données en mémoire cache, les contrôles liés aux données sont synchronisés automatiquement avec les modifications et l'utilisateur voit apparaître les données mises à jour.  Pour plus d’informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel et Word ne sont pas nécessaires pour modifier les données sur le serveur, mais uniquement pour les afficher sur le client.  Il est même inutile d'installer Excel et Word sur le serveur.  Cette procédure améliore l'extensibilité et accélère le traitement par lots des documents contenant des îlots de données.  
  
## Mise en cache des données pour une utilisation hors connexion  
 Stocker des données dans des îlots de données permet des scénarios hors connexion.  Lorsque, pour la première fois, un utilisateur ouvre un document ou le demande à partir du serveur, l'îlot de données est rempli avec les données les plus récentes.  L'îlot de données est mis en cache dans le document et devient alors disponible hors connexion.  L'utilisateur \(et votre code\) peuvent manipuler les données, bien qu'aucune connexion active ne soit disponible.  Lorsque l'utilisateur se reconnecte, les modifications apportées aux données peuvent être retournées à une source de données serveur.  
  
## Comparaison des données en mémoire cache et parties XML personnalisées  
 Les parties XML personnalisées ont été introduites dans la version 2007 de Microsoft Office System comme une méthode permettant de stocker des fragments arbitraires de code XML dans un document.  Les parties XML personnalisées sont utiles dans plus ou moins les mêmes scénarios que le cache de données, toutefois, il existe des différences entre l'îlot des données et les parties XML personnalisées.  Pour plus d'informations sur les parties XML personnalisées, consultez [Vue d'ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).  
  
 Le tableau suivant répertorie quelques différences et points communs.  
  
||Cache de données|Parties XML personnalisées|  
|-|----------------------|--------------------------------|  
|Quelles sont les applications Office qui peuvent les utiliser ?|Personnalisations au niveau du document pour les applications suivantes :<br /><br /> -   Excel<br />-   Word|Solutions au niveau du document et au niveau de l'application pour les applications suivantes :<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|  
|Quels sont les types de données qui peuvent y être enregistrés ?|Tout objet public de votre assembly de personnalisation répondant à certaines exigences.  Pour plus d’informations, consultez [Mise en cache des données](../vsto/caching-data.md).|Toutes les données XML.|  
|Est\-il possible d'accéder aux données sans démarrer des applications Microsoft Office ?|Oui, en utilisant la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> fournie par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Oui, en utilisant les classes de l'espace de noms <xref:System.IO.Packaging> ou en utilisant le Kit de développement logiciel du format Open XML.|  
  
## Voir aussi  
 [Données dans les solutions Office](../vsto/data-in-office-solutions.md)   
 [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  