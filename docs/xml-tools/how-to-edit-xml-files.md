---
title: "Proc&#233;dure&#160;: modifier des fichiers XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: modifier des fichiers XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'éditeur XML est le nouvel éditeur pour les fichiers XML.Il peut être utilisé avec un fichier XML autonome ou un fichier associé à un projet Visual Studio.L'Éditeur XML est associé aux extensions de fichier suivantes : .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt et .vssettings.L'éditeur XML est également associé à tout autre type de fichier qui n'a pas d'éditeur spécifique défini et dont le contenu est du XML ou une DTD.  
  
> [!NOTE]
>  Les documents XHTML sont traités dans l'éditeur HTML.  
  
### Pour modifier un fichier XML  
  
1.  Double\-cliquez sur le fichier à modifier.  
  
### Pour ajouter un nouveau fichier XML à un projet  
  
1.  Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.  
  
2.  Sélectionnez **Fichier XML** dans le volet **Modèles**.  
  
3.  Entrez le nom du fichier dans le champ **Nom** et cliquez sur **Ajouter**.  
  
     Le fichier XML est ajouté au projet et ouvert dans l'éditeur XML.Il contient la déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### Pour ajouter un fichier XML existant à un projet  
  
1.  Dans le menu **Projet**, sélectionnez **Ajouter un élément existant**.  
  
     La boîte de dialogue **Ajouter un élément existant** s'affiche.  
  
2.  Sélectionnez un fichier XML et cliquez sur **Ajouter**.  
  
### Pour créer un nouveau fichier XML ou XSLT  
  
1.  Dans le menu **Fichier**, sélectionnez **Nouveau**.  
  
     La boîte de dialogue **Nouveau fichier** s'affiche.  
  
2.  Sélectionnez **Fichier XML** pour créer un nouveau fichier XML ou **Fichier XSLT** pour créer une nouvelle feuille de style XSLT.  
  
3.  Cliquez sur **Ouvrir**.  
  
### Pour créer un projet pour des fichiers XML  
  
1.  Dans le menu **Fichier**, sélectionnez **Nouveau**, puis **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sélectionnez le langage de code de votre choix, puis **Projet vide** et cliquez sur **OK**.  
  
3.  Ajoutez des fichiers XML au projet.  
  
     L'éditeur XML recherche les schémas ajoutés à ce projet et les utilise pour la validation et les fonctions IntelliSense dans tout fichier XML, de schéma ou XSLT que vous éditez alors que ce projet est ouvert.  
  
## Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)   
 [Propriétés des documents XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)   
 [Procédure : créer un schéma XML à partir d'un document XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)