---
title: 'Procédure : Exécuter une Transformation XSLT à partir de l’éditeur XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cf4696827f0c94e9eb9dfbd88a5e814298f823e1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649522"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procédure : Exécuter une transformation XSLT à partir de l’éditeur XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'Éditeur XML permet d'associer une feuille de style XSLT à un document XML, d'effectuer la transformation et d'en afficher le résultat. Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.  
  
 Le **sortie** propriété spécifie le nom de fichier pour la sortie. Si le **sortie** propriété est vide, un nom de fichier est généré dans votre répertoire temporaire. L'extension du fichier est basée sur l'élément `xsl:output` de votre feuille de style et peut être .xml, .txt ou .htm.  
  
 Si le **sortie** propriété spécifie un nom de fichier avec un .htm ou .html extension, la sortie XSLT est prévisualisée [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Toutes les autres extensions de fichier s’ouvrent dans l’éditeur par défaut choisi par [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio. Par exemple, si l'extension de fichier est .xml, Visual Studio utilise l'éditeur XML.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Pour exécuter une transformation XSLT à partir d'un document XML  
  
1.  Ouvrez un document XML dans l'éditeur XML.  
  
2.  Associez une feuille de style XSLT au document XML.  
  
    -   Ajoutez une instruction de traitement `xml-stylesheet` au document XML. Par exemple, ajoutez la ligne `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` au prologue du document.  
  
         - ou -  
  
    -   Ajouter la feuille de style XSLT à l’aide du **propriétés** fenêtre. Dans le document **fenêtre Propriétés**, cliquez sur le **Parcourir** bouton pour le **feuille de style** champ, sélectionnez la feuille de style XSLT, puis cliquez sur **ouvrir**.  
  
3.  Cliquez sur le **ShowXSL sortie** bouton sur le **éditeur XML** barre d’outils.  
  
    > [!NOTE]
    >  Si aucune feuille de style n'est associée au document XML, une boîte de dialogue vous invite à la spécifier.  
    >   
    >  Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Pour exécuter une transformation XSLT à partir d'une feuille de style XSLT  
  
1.  Ouvrez une feuille de style XSLT dans l'éditeur XML.  
  
2.  Spécifiez un document XML dans le **entrée** champ du document **propriétés** fenêtre.  
  
    > [!NOTE]
    >  Le document XML est le document d'entrée utilisé pour la transformation. Si un document n’est pas spécifié lors de la transformation XSLT est démarrée, le **ouvrir le fichier** boîte de dialogue s’affiche et vous pouvez spécifier un document à ce moment-là.  
  
3.  Cliquez sur le **ShowXSLT sortie** bouton sur le **éditeur XML** barre d’outils.  
  
     Le résultat de la transformation XSLT est affiché dans une nouvelle fenêtre de document.  
  
### <a name="to-provide-a-different-output-file-name"></a>Pour spécifier un autre nom de fichier de sortie  
  
1.  Spécifiez un nom de fichier dans le **sortie** champ du document **propriétés** fenêtre.  
  
2.  Cliquez sur le **ShowXSLT sortie** bouton sur le **éditeur XML** barre d’outils.  
  
     Le résultat de la transformation XSLT s’affiche dans une nouvelle fenêtre de document et de l’éditeur utilisé dans la fenêtre de sortie dépend de l’extension de fichier de votre **sortie** propriété de document.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)
