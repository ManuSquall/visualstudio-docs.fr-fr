---
title: "D&#233;cisions de conception du contr&#244;le source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), les décisions de conception"
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# D&#233;cisions de conception du contr&#244;le source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les décisions de conception suivantes doivent être considérées comme des projets en implémentant le contrôle de code source.  
  
## les informations seront\-elles partagées ou privées ?  
 Est la décision de conception la plus importante que vous pouvez récupérer ce qui les informations sont partageables et ce qui est privé.  Par exemple, la liste des fichiers du projet est partagée, mais dans cette liste des fichiers, certains utilisateurs peuvent avoir besoin des fichiers privés.  Les paramètres de compilateur sont partagés, mais le projet de démarrage est généralement privé.  Les paramètres ou sont purement partagés, partagés avec une substitution, ou purement privé.  Par conception, les éléments privés, tels que les fichiers des options d'utilisateur de solution \(.suo\), ne sont pas activées dans [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)].  Veillez à stocker les informations confidentielles dans les fichiers privés tels que le fichier .suo, ou un fichier privé spécifique que vous créez, par exemple, un fichier .csproj.user pour Visual c\# ou un fichier .vbproj.user pour Visual Basic.  
  
 Cette décision n'est pas inclusive et peut être effectuée sur un élément par élément.  
  
## le projet comprendra\-il des fichiers spéciaux ?  
 Une autre décision de conception importante est si votre structure de projet utilise les fichiers spéciaux.  Les fichiers spéciaux sont des fichiers masqués qui sont à la base des fichiers qui se trouvent dans l'explorateur de solutions et dans les boîtes de dialogue d'archivage et d'extraction.  Si vous utilisez des fichiers spéciaux, suivez les indications ci\-après :  
  
1.  N'associez pas les fichiers spéciaux avec la racine du projet nœud\-qu'est, avec le fichier projet lui\-même.  votre fichier projet doit être un fichier unique.  
  
2.  Lorsque les fichiers spéciaux sont ajoutés, supprimés ou renommés, dans un projet, les événements appropriés pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> doivent être déclenchés avec l'indicateur défini qui indique les fichiers sont des fichiers spéciaux.  Ces événements sont appelés par l'environnement en réponse à le projet appelant les méthodes appropriées de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .  
  
3.  Lorsque votre projet ou éditeur appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> d'un fichier, les fichiers spécifiques sont associés à ce fichier ne sont pas extraits automatiquement.  Passez les fichiers spéciaux de l'avec le fichier parent.  L'environnement détecte la relation entre tous les fichiers qui sont passés dans et masquer correctement les fichiers spéciaux du contrôle interface utilisateur.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Prise en charge du contrôle de code Source](../../extensibility/internals/supporting-source-control.md)