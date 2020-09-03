---
title: 'Procédure : exécuter une transformation XSLT à partir de l’éditeur XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666535"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procédure : exécuter une transformation XSLT à partir de l'Éditeur XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'Éditeur XML permet d'associer une feuille de style XSLT à un document XML, d'effectuer la transformation et d'en afficher le résultat. Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.

 La propriété **Output** spécifie le nom de fichier de la sortie. Si la propriété de **sortie** est vide, un nom de fichier est généré dans votre répertoire temporaire. L'extension du fichier est basée sur l'élément `xsl:output` de votre feuille de style et peut être .xml, .txt ou .htm.

 Si la propriété **Output** spécifie un nom de fichier avec une extension. htm ou. html, la sortie XSLT est prévisualisée à l’aide d' [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Toutes les autres extensions de fichier s’ouvrent dans l’éditeur par défaut choisi par [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio. Par exemple, si l'extension de fichier est .xml, Visual Studio utilise l'éditeur XML.

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Pour exécuter une transformation XSLT à partir d'un document XML

1. Ouvrez un document XML dans l'éditeur XML.

2. Associez une feuille de style XSLT au document XML.

    - Ajoutez une instruction de traitement `xml-stylesheet` au document XML. Par exemple, ajoutez la ligne `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` au prologue du document.

         - ou -

    - Ajoutez la feuille de style XSLT à l’aide de la fenêtre **Propriétés** . Dans la **fenêtre Propriétés**du document, cliquez sur le bouton **Parcourir** pour le champ **feuille** de style, sélectionnez la feuille de style XSLT, puis cliquez sur **ouvrir**.

3. Cliquez sur le bouton **sortie de ShowXSL** dans la barre d’outils de l' **éditeur XML** .

    > [!NOTE]
    > Si aucune feuille de style n'est associée au document XML, une boîte de dialogue vous invite à la spécifier.
    >
    >  Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Pour exécuter une transformation XSLT à partir d'une feuille de style XSLT

1. Ouvrez une feuille de style XSLT dans l'éditeur XML.

2. Spécifiez un document XML dans le champ **entrée** de la fenêtre **Propriétés** du document.

    > [!NOTE]
    > Le document XML est le document d'entrée utilisé pour la transformation. Si un document n’est pas spécifié lors du démarrage de la transformation XSLT, la boîte de dialogue **ouvrir un fichier** s’affiche et vous pouvez spécifier un document à ce moment-là.

3. Cliquez sur le bouton **sortie de ShowXSLT** dans la barre d’outils de l' **éditeur XML** .

     Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.

### <a name="to-provide-a-different-output-file-name"></a>Pour spécifier un autre nom de fichier de sortie

1. Spécifiez un nom de fichier dans le champ **sortie** de la fenêtre **Propriétés** du document.

2. Cliquez sur le bouton **sortie de ShowXSLT** dans la barre d’outils de l' **éditeur XML** .

     Le résultat de la transformation XSLT s’affiche dans une nouvelle fenêtre de document et l’éditeur utilisé dans la fenêtre de sortie dépend de l’extension de fichier de votre propriété de document de **sortie** .

## <a name="see-also"></a>Voir aussi
 [Éditeur XML](../xml-tools/xml-editor.md)
