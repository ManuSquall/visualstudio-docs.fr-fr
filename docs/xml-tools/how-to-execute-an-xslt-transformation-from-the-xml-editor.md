---
title: Exécuter une transformation XSLT
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e74beb2903cd133dfdd322ce4c297692eae3411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817188"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procédure : exécuter une transformation XSLT à partir de l’éditeur XML

L’éditeur XML vous permet d’associer une feuille de style XSLT à un document XML, d’effectuer la transformation et d’afficher la sortie. Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.

La propriété **Output** spécifie le nom de fichier de la sortie. Si la propriété de **sortie** est vide, un nom de fichier est généré dans votre répertoire temporaire. L’extension de fichier est basée sur l' `xsl:output` élément de votre feuille de style et peut être.* XML*,. *txt* ou. *htm*.

Si la propriété de **sortie** spécifie un nom de fichier avec un. *htm* ou. extension *HTML* , la sortie XSLT est prévisualisée à l’aide d’un navigateur Web. Toutes les autres extensions de fichier sont ouvertes à l’aide de l’éditeur par défaut choisi par Visual Studio. Par exemple, si l’extension de fichier est. *XML*, Visual Studio utilise l’éditeur XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Exécuter une transformation XSLT à partir d’un fichier XML

1. Ouvrez un document XML dans l’éditeur XML.

2. Associez une feuille de style XSLT au document XML.

    - Ajoutez une instruction de traitement `xml-stylesheet` au document XML. Par exemple, ajoutez la ligne suivante au prologue du document : `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       - ou -

    - Ajoutez la feuille de style XSLT à l’aide de la fenêtre **Propriétés** . Après avoir ouvert le fichier XML dans l’éditeur, cliquez avec le bouton droit n’importe où dans l’éditeur et choisissez **Propriétés**. Dans la fenêtre **Propriétés** , cliquez dans le champ **feuille de style** et choisissez le bouton Parcourir (...). Sélectionnez la feuille de style XSLT, puis choisissez **ouvrir**.

3. Dans la barre de menus, choisissez **XML**  >  **Démarrer XSLT sans débogage**. Ou appuyez sur **CTRL** + **ALT** + **F5**.

   La sortie de la transformation XSLT s’affiche dans une nouvelle fenêtre de document.

   > [!NOTE]
   > Si aucune feuille de style n'est associée au document XML, une boîte de dialogue vous invite à la spécifier.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Exécuter une transformation XSLT à partir d’une feuille de style XSLT

1. Ouvrez une feuille de style XSLT dans l’éditeur XML.

2. Spécifiez un document XML dans le champ **entrée** de la fenêtre **Propriétés** du document.

   > [!NOTE]
   > Le document XML est le document d'entrée utilisé pour la transformation. Si aucun document n’est spécifié lors du démarrage de la transformation XSLT, la boîte de dialogue **ouvrir un fichier** s’affiche et vous pouvez spécifier un document à ce moment-là.

3. Dans la barre de menus, choisissez **XML**  >  **Démarrer XSLT sans débogage**. Ou appuyez sur **CTRL** + **ALT** + **F5**.

   La sortie de la transformation XSLT s’affiche dans une nouvelle fenêtre de document.

## <a name="specify-an-output-file-name"></a>Spécifier un nom de fichier de sortie

Vous pouvez spécifier un nom de fichier de sortie pour les fichiers XML et XSL. Ouvrez la fenêtre **Propriétés** et spécifiez un nom de fichier dans le champ de **sortie** .

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
