---
title: 'Procédure : modifier des fichiers XML'
ms.date: 11/04/2016
description: Découvrez comment utiliser l’éditeur XML dans Visual Studio pour modifier des fichiers qui contiennent du contenu XML ou DTD.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c538e9a4da3c4bbd08c571818dbaaaca466c2471
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948542"
---
# <a name="how-to-edit-xml-files"></a>Comment : modifier des fichiers XML

L’éditeur XML est le nouvel éditeur pour les fichiers XML. Il peut être utilisé avec un fichier XML autonome ou un fichier associé à un projet Visual Studio. L’éditeur XML est associé aux extensions de fichier suivantes : *. config*, *. DTD*, *. xml*, *. xsd*,. *XDR*,. *xsl*, *. XSLT* et *. vssettings*. L’éditeur XML est également associé à tout autre type de fichier pour lequel aucun éditeur spécifique n’est inscrit, et qui contient du contenu XML ou DTD.

> [!NOTE]
> Les documents XHTML sont traités dans l'éditeur HTML.

Pour modifier un fichier XML, ouvrez le fichier que vous souhaitez modifier.

## <a name="add-a-new-xml-file-to-a-project"></a>Ajouter un nouveau fichier XML à un projet

1. Dans le menu **projet** , sélectionnez **Ajouter un nouvel élément**.

2. Sélectionnez **fichier XML** dans le volet **modèles** .

3. Entrez le nom du fichier dans le champ **nom** , puis appuyez sur **Ajouter**.

   Le fichier XML est ajouté au projet et s’ouvre dans l’éditeur XML. Il contient la déclaration XML par défaut, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Ajouter un fichier XML existant à un projet

1. Dans le menu **Projet**, sélectionnez **Ajouter un élément existant**.

   La boîte de dialogue **Ajouter un élément existant** s’affiche.

2. Sélectionnez un fichier XML et appuyez sur **Ajouter**.

## <a name="create-a-new-xml-or-xslt-file"></a>Créer un nouveau fichier XML ou XSLT

1. Dans le menu **Fichier**, cliquez sur **Nouveau**.

   La boîte de dialogue **Nouveau fichier** s'affiche.

2. Sélectionnez **fichier XML** pour créer un nouveau fichier XML. ou sélectionnez **fichier XSLT** pour créer une nouvelle feuille de style XSLT.

3. Sélectionnez **Ouvrir**.

## <a name="create-an-empty-project-for-xml-files"></a>Créer un projet vide pour les fichiers XML

::: moniker range="vs-2017"

1. Dans le menu **fichier** , sélectionnez **nouveau** > **projet**.

   La boîte de dialogue **Nouveau projet** apparaît.

2. Sélectionnez le langage de code de votre choix, puis sélectionnez le modèle **projet vide (.NET Framework)** .

3. Sélectionnez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans le menu **fichier** , sélectionnez **nouveau** > **projet**.

2. Entrez un **projet vide** dans la zone de recherche du modèle, sélectionnez le modèle **projet vide (.NET Framework)** , puis sélectionnez **suivant**.

3. Sélectionnez **Create** (Créer).

::: moniker-end

4. Ajoutez des fichiers XML au projet.

   L’éditeur XML recherche les schémas que vous ajoutez à ce projet et les utilise pour la validation et IntelliSense dans tout fichier XML, de schéma ou XSLT que vous modifiez alors que ce projet est ouvert.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
- [Propriétés du document XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)
- [Procédure : créer un schéma XML à partir d’un document XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
