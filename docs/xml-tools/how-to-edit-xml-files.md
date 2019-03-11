---
title: 'Procédure : modification de fichiers XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7da94f8fe07620a67e2df8876cf1d3adda443c5
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525451"
---
# <a name="how-to-edit-xml-files"></a>Procédure : Modifier des fichiers XML

L’éditeur XML est le nouvel éditeur pour les fichiers XML. Il peut être utilisé avec un fichier XML autonome ou un fichier associé à un projet Visual Studio. L’éditeur XML est associé aux extensions de fichier suivantes : *.config*, *.dtd*, *.xml*, *.xsd*, *.xdr*, *.xsl*, *.xslt*, et *.vssettings*. L’éditeur XML est également associé à n’importe quel autre type de fichier qui n’a aucun éditeur spécifique inscrit, et qui contient le contenu XML ou une DTD.

> [!NOTE]
> Les documents XHTML sont traités dans l'éditeur HTML.

## <a name="to-edit-an-xml-file"></a>Pour modifier un fichier XML

1.  Double-cliquez sur le fichier à modifier.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Pour ajouter un nouveau fichier XML à un projet

1.  À partir de la **projet** menu, sélectionnez **ajouter un nouvel élément**.

2.  Sélectionnez **fichier XML** à partir de la **modèles** volet.

3.  Entrez le nom de fichier dans le **nom** champ et appuyez sur **ajouter**.

     Le fichier XML est ajouté au projet et ouvert dans l’éditeur XML. Il contient la déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="to-add-an-existing-xml-file-to-a-project"></a>Pour ajouter un fichier XML existant à un projet

1.  À partir de la **projet** menu, sélectionnez **ajouter un élément existant**.

     Le **ajouter un élément existant** boîte de dialogue s’affiche.

2.  Sélectionnez un fichier XML et la presse **ajouter**.

## <a name="to-create-a-new-xml-or-xslt-file"></a>Pour créer un nouveau fichier XML ou XSLT

1.  À partir de la **fichier** menu, sélectionnez **New**.

     Le **nouveau fichier** boîte de dialogue s’affiche.

2.  Sélectionnez **fichier XML** pour créer un nouveau fichier XML ; ou, sélectionnez **fichier XSLT** pour créer une nouvelle feuille de style XSLT.

3.  Cliquez sur **Ouvrir**.

## <a name="to-create-a-project-for-xml-files"></a>Pour créer un projet pour des fichiers XML

1.  À partir de la **fichier** menu, sélectionnez **New**, puis sélectionnez **projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

2.  Sélectionnez le langage de code de votre choix, sélectionnez **projet vide**, puis cliquez sur **OK**.

3.  Ajoutez des fichiers XML au projet.

     L’éditeur XML recherche les schémas que vous ajoutez à ce projet et les utilise pour la validation et IntelliSense dans n’importe quel schéma, XML ou fichiers XSLT que vous modifiez alors que ce projet est ouvert.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
- [Propriétés des documents XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)
- [Guide pratique pour Créer un schéma XML à partir d’un document XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)