---
title: 'Procédure : Modifier des fichiers XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 92f233a036c3c0b40cbd53a298154919861b58b8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663659"
---
# <a name="how-to-edit-xml-files"></a>Procédure : modification de fichiers XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'éditeur XML est le nouvel éditeur pour les fichiers XML. Il peut être utilisé avec un fichier XML autonome ou un fichier associé à un projet Visual Studio. L'Éditeur XML est associé aux extensions de fichier suivantes : .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt et .vssettings. L'éditeur XML est également associé à tout autre type de fichier qui n'a pas d'éditeur spécifique défini et dont le contenu est du XML ou une DTD.  
  
> [!NOTE]
>  Les documents XHTML sont traités dans l'éditeur HTML.  
  
### <a name="to-edit-an-xml-file"></a>Pour modifier un fichier XML  
  
1.  Double-cliquez sur le fichier à modifier.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>Pour ajouter un nouveau fichier XML à un projet  
  
1.  À partir de la **projet** menu, sélectionnez **ajouter un nouvel élément**.  
  
2.  Sélectionnez **fichier XML** à partir de la **modèles** volet.  
  
3.  Entrez le nom de fichier dans le **nom** champ et appuyez sur **ajouter**.  
  
     Le fichier XML est ajouté au projet et ouvert dans l'éditeur XML. Il contient la déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>Pour ajouter un fichier XML existant à un projet  
  
1.  À partir de la **projet** menu, sélectionnez **ajouter un élément existant**.  
  
     Le **ajouter un élément existant** boîte de dialogue s’affiche.  
  
2.  Sélectionnez un fichier XML et la presse **ajouter**.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>Pour créer un nouveau fichier XML ou XSLT  
  
1.  À partir de la **fichier** menu, sélectionnez **New**.  
  
     Le **nouveau fichier** boîte de dialogue s’affiche.  
  
2.  Sélectionnez **fichier XML** pour créer un nouveau fichier XML ; ou, sélectionnez **fichier XSLT** pour créer une nouvelle feuille de style XSLT.  
  
3.  Cliquez sur **Ouvrir**.  
  
### <a name="to-create-a-project-for-xml-files"></a>Pour créer un projet pour des fichiers XML  
  
1.  À partir de la **fichier** menu, sélectionnez **New**, puis sélectionnez **projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Sélectionnez le langage de code de votre choix, sélectionnez **projet vide**, puis cliquez sur **OK**.  
  
3.  Ajoutez des fichiers XML au projet.  
  
     L'éditeur XML recherche les schémas ajoutés à ce projet et les utilise pour la validation et les fonctions IntelliSense dans tout fichier XML, de schéma ou XSLT que vous éditez alors que ce projet est ouvert.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)   
 [Propriétés des documents XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)   
 [Guide pratique pour Créer un schéma XML à partir d’un document XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
