---
title: 'Comment : modifier des fichiers XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c099839cda87819ec0ec7932c2b2e6aa7698fa52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670883"
---
# <a name="how-to-edit-xml-files"></a>Procédure : modifier des fichiers XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'éditeur XML est le nouvel éditeur pour les fichiers XML. Il peut être utilisé avec un fichier XML autonome ou un fichier associé à un projet Visual Studio. L'Éditeur XML est associé aux extensions de fichier suivantes : .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt et .vssettings. L'éditeur XML est également associé à tout autre type de fichier qui n'a pas d'éditeur spécifique défini et dont le contenu est du XML ou une DTD.

> [!NOTE]
> Les documents XHTML sont traités dans l'éditeur HTML.

### <a name="to-edit-an-xml-file"></a>Pour modifier un fichier XML

1. Double-cliquez sur le fichier à modifier.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Pour ajouter un nouveau fichier XML à un projet

1. Dans le menu **projet** , sélectionnez **Ajouter un nouvel élément**.

2. Sélectionnez **fichier XML** dans le volet **modèles** .

3. Entrez le nom du fichier dans le champ **nom** , puis appuyez sur **Ajouter**.

     Le fichier XML est ajouté au projet et ouvert dans l'éditeur XML. Il contient la déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8" ?>`.

### <a name="to-add-an-existing-xml-file-to-a-project"></a>Pour ajouter un fichier XML existant à un projet

1. Dans le menu **Projet**, sélectionnez **Ajouter un élément existant**.

     La boîte de dialogue **Ajouter un élément existant** s’affiche.

2. Sélectionnez un fichier XML et appuyez sur **Ajouter**.

### <a name="to-create-a-new-xml-or-xslt-file"></a>Pour créer un nouveau fichier XML ou XSLT

1. Dans le menu **Fichier**, cliquez sur **Nouveau**.

     La boîte de dialogue **Nouveau fichier** s'affiche.

2. Sélectionnez **fichier XML** pour créer un nouveau fichier XML. ou sélectionnez **fichier XSLT** pour créer une nouvelle feuille de style XSLT.

3. Cliquez sur **Ouvrir**.

### <a name="to-create-a-project-for-xml-files"></a>Pour créer un projet pour des fichiers XML

1. Dans le menu **Fichier**, sélectionnez **Nouveau**, puis **Projet**.

     La boîte de dialogue **Nouveau projet** apparaît.

2. Sélectionnez le langage de code de votre choix, sélectionnez **projet vide**, puis cliquez sur **OK**.

3. Ajoutez des fichiers XML au projet.

     L'éditeur XML recherche les schémas ajoutés à ce projet et les utilise pour la validation et les fonctions IntelliSense dans tout fichier XML, de schéma ou XSLT que vous éditez alors que ce projet est ouvert.

## <a name="see-also"></a>Voir aussi
 Propriétés du document XML de l' [éditeur XML](../xml-tools/xml-editor.md) [, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md) [Comment : créer un schéma XML à partir d’un document XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
