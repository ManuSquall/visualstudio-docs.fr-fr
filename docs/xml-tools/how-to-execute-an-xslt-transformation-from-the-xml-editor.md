---
title: Exécuter une transformation XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84b1c6303da4c0db39da1b3585a7d4548560feb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001935"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procédure : Exécuter une transformation XSLT à partir de l’éditeur XML

L’éditeur XML vous permet d’associer une feuille de style XSLT à un document XML, effectuer la transformation et afficher la sortie. Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.

Le **sortie** propriété spécifie le nom de fichier pour la sortie. Si le **sortie** propriété est vide, un nom de fichier est généré dans votre répertoire temporaire. L’extension de fichier est basée sur le `xsl:output` élément dans votre style de la feuille et peut être. *XML*,. *txt* ou. *htm*.

Si le **sortie** propriété spécifie un nom de fichier avec une. *htm* ou. *HTML* extension, la sortie XSLT est affichée à l’aide d’un navigateur web. Toutes les autres extensions de fichiers sont ouverts à l’aide de l’éditeur par défaut choisi par Visual Studio. Par exemple, si l’extension de fichier est. *xml*, Visual Studio utilise l’éditeur XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Exécuter une transformation XSLT à partir d’un fichier XML

1. Ouvrez un document XML dans l’éditeur XML.

2. Associez une feuille de style XSLT au document XML.

    - Ajoutez une instruction de traitement `xml-stylesheet` au document XML. Par exemple, ajoutez la ligne suivante au prologue du document : `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       - ou -

    - Ajouter la feuille de style XSLT à l’aide du **propriétés** fenêtre. Le fichier XML ouvert dans l’éditeur, avec le bouton droit n’importe où dans l’éditeur et choisissez **propriétés**. Dans le **propriétés** fenêtre, cliquez dans le **feuille de style** champ et cliquez sur le bouton Parcourir (...). Sélectionnez la feuille de style XSLT, puis **Open**.

3. Dans la barre de menus, choisissez **XML** > **démarrer sans débogage XSLT**. Ou bien, appuyez sur **Ctrl**+**Alt**+**F5**.

   La sortie de la transformation XSLT s’affiche dans une nouvelle fenêtre de document.

   > [!NOTE]
   > Si aucune feuille de style n'est associée au document XML, une boîte de dialogue vous invite à la spécifier.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Exécuter une transformation XSLT à partir d’une feuille de style XSLT

1. Ouvrez une feuille de style XSLT dans l’éditeur XML.

2. Spécifiez un document XML dans le **entrée** champ du document **propriétés** fenêtre.

   > [!NOTE]
   > Le document XML est le document d'entrée utilisé pour la transformation. Si un document n’est pas spécifié lors de la transformation XSLT est démarrée, le **ouvrir le fichier** boîte de dialogue s’affiche et vous pouvez spécifier un document à ce moment-là.

3. Dans la barre de menus, choisissez **XML** > **démarrer sans débogage XSLT**. Ou bien, appuyez sur **Ctrl**+**Alt**+**F5**.

   La sortie de la transformation XSLT s’affiche dans une nouvelle fenêtre de document.

## <a name="specify-an-output-file-name"></a>Spécifiez un nom de fichier de sortie

Vous pouvez spécifier un nom de fichier de sortie pour les fichiers XML et XSL. Ouvrez le **propriétés** fenêtre et spécifiez un nom de fichier dans le **sortie** champ.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)