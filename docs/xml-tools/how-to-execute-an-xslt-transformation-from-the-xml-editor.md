---
title: "Proc&#233;dure&#160;: ex&#233;cuter une transformation XSLT &#224; partir de l&#39;&#201;diteur XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: ex&#233;cuter une transformation XSLT &#224; partir de l&#39;&#201;diteur XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'Éditeur XML permet d'associer une feuille de style XSLT à un document XML, d'effectuer la transformation et d'en afficher le résultat.Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.  
  
 La propriété **Output** spécifie le nom de fichier de la sortie.Si cette propriété est vide, un nom de fichier est généré dans votre répertoire temporaire.L'extension du fichier est basée sur l'élément `xsl:output` de votre feuille de style et peut être .xml, .txt ou .htm.  
  
 Si la propriété **Output** spécifie un nom de fichier avec une extension .htm ou .html, la sortie XSLT est prévisualisée dans [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer.Toutes les autres extensions de fichier s'ouvrent dans l'éditeur par défaut choisi par [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio.Par exemple, si l'extension de fichier est .xml, Visual Studio utilise l'éditeur XML.  
  
### Pour exécuter une transformation XSLT à partir d'un document XML  
  
1.  Ouvrez un document XML dans l'éditeur XML.  
  
2.  Associez une feuille de style XSLT au document XML.  
  
    -   Ajoutez une instruction de traitement `xml-stylesheet` au document XML.Par exemple, ajoutez la ligne `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` au prologue du document.  
  
         \-ou\-  
  
    -   Ajoutez la feuille de style XSLT à l'aide de la fenêtre **Propriétés**.Dans la fenêtre**Propriétés** du document, cliquez sur le bouton **Parcourir** du champ **Feuille de style**, sélectionnez la feuille de style XSLT et cliquez sur **Ouvrir**.  
  
3.  Cliquez sur le bouton **Afficher la sortie XSLT** dans la barre d'outils **Éditeur XML**.  
  
    > [!NOTE]
    >  Si aucune feuille de style n'est associée au document XML, une boîte de dialogue vous invite à la spécifier.  
    >   
    >  Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.  
  
### Pour exécuter une transformation XSLT à partir d'une feuille de style XSLT  
  
1.  Ouvrez une feuille de style XSLT dans l'éditeur XML.  
  
2.  Spécifiez un document XML dans le champ **Entrée** de la fenêtre **Propriétés** du document.  
  
    > [!NOTE]
    >  Le document XML est le document d'entrée utilisé pour la transformation.Si aucun document n'est spécifié lorsque la transformation XSLT commence, la boîte de dialogue **Ouvrir un fichier** s'affiche, vous permettant de spécifier un document à ce moment\-là.  
  
3.  Cliquez sur le bouton **Afficher la sortie XSLT** dans la barre d'outils **Éditeur XML**.  
  
     Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.  
  
### Pour spécifier un autre nom de fichier de sortie  
  
1.  Spécifiez un nom de fichier dans le champ **Sortie** de la fenêtre **Propriétés** du document.  
  
2.  Cliquez sur le bouton **Afficher la sortie XSLT** dans la barre d'outils **Éditeur XML**.  
  
     Le résultat de la transformation XSLT s'affiche dans une nouvelle fenêtre de document ; l'éditeur utilisé dans la fenêtre de sortie dépend de l'extension de fichier de votre propriété de document **Output**.  
  
## Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)