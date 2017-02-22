---
title: "How to: Specify Where Visual Studio Copies the Files | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "publishing, specifying location"
  - "Publish Location property"
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Specify Where Visual Studio Copies the Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quand vous publiez une application à l'aide de ClickOnce, la propriété `Publish Location` indique l'emplacement de destination des fichiers d'application et du manifeste.  Il peut s'agir d'un chemin d'accès de fichier ou du chemin d'accès à un serveur FTP.  
  
 Vous pouvez spécifier la propriété `Publish Location` dans la page **Publier** du **Concepteur de projets** ou en utilisant l'Assistant Publication.  Pour plus d'informations, consultez [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
> [!NOTE]
>  Quand vous installez plusieurs versions d'une application via ClickOnce, l'installation déplace les versions antérieures de cette application dans un dossier nommé Archive, à l'emplacement de publication que vous avez spécifié.  Cet archivage permet d'éviter la présence de dossiers de la version précédente dans le répertoire d'installation.  
  
### Pour spécifier un emplacement de publication  
  
1.  Après avoir sélectionné un projet dans l'**Explorateur de solutions**, dans le menu **Projet**, cliquez sur **Propriétés**.  
  
2.  Cliquez sur l'onglet **Publier**.  
  
3.  Dans le champ **Emplacement de publication**, entrez l'emplacement de publication dans l'un des formats suivants :  
  
    -   Pour publier vers un partage de fichiers ou un chemin d'accès de disque, entrez le chemin d'accès sous forme de chemin d'accès UNC \(\\\\Serveur\\Nom\_application\) ou de chemin d'accès de fichier \(C:\\Déploiement\\Nom\_application\).  
  
    -   Pour publier vers un serveur FTP, entrez le chemin d'accès dans le format suivant : ftp:\/\/ftp.microsoft.com\/Nom\_application.  
  
     Notez que le texte doit figurer dans la zone **Emplacement de publication** pour que le bouton de navigation \(**...**\) fonctionne.  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)