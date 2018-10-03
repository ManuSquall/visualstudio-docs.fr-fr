---
title: Propriétés des documents XML, fenêtre Propriétés | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7145c81a87235d37a0e4825509e7f8fb94ab0f7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508650"
---
# <a name="xml-document-properties-properties-window"></a>Propriétés des documents XML, fenêtre Propriétés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [propriétés des documents XML, fenêtre Propriétés](https://docs.microsoft.com/visualstudio/xml-tools/xml-document-properties-properties-window).  
  
  
Le **propriétés** fenêtre fournit des informations de base sur le document est actif dans l’éditeur XML. Les propriétés disponibles varient selon le type de document XML actif.  
  
> [!NOTE]
>  Toutes les propriétés des documents XML sont enregistrées dans la solution. Vous ne devez donc pas réentrer ces valeurs la prochaine fois que vous ouvrez la solution.  
  
 **Encodage**  
 Encodage de caractères utilisé pour le fichier. La modification de cette propriété entraîne la modification de l'attribut d'encodage dans la déclaration XML et vice versa. Le nouvel encodage permet de coder le fichier lors de son enregistrement.  
  
 **Entrée**  
 Document d'entrée associé à la feuille de style XSLT. Il est utilisé par le **ShowXSLT sortie** commande. Un document peut être sélectionné à l’aide de la navigation (**...** ) bouton.  
  
 Cette propriété n'est visible que lorsqu'un fichier XSLT est actif dans la fenêtre de l'éditeur.  
  
 **Sortie**  
 Fichier généré lors de la transformation d'un document XML.  
  
 Si aucun fichier n'est spécifié, un nom de fichier par défaut est généré d'après l'attribut `method` de l'élément `xsl:output`, qui détermine l'extension du fichier. Le fichier par défaut se situe dans le répertoire temporaire de l'utilisateur actuel.  
  
 **Schémas**  
 Schémas utilisés pour la validation. Le bouton ouvre le **schémas XSD** boîte de dialogue, qui peut être utilisé pour sélectionner les schémas à utiliser.  
  
 Il permet également d’entrer le chemin des schémas. Si plusieurs schémas sont spécifiés, le chemin de chacun doit être placé entre des guillemets doubles.  
  
 **Feuille de style**  
 Le fichier XSLT utilisé pour transformer le document lorsque le **afficher la sortie XSLT** commande est utilisée. Si ce champ est vide lorsque le **afficher la sortie XSLT** commande est utilisée, l’éditeur utilise la valeur fournie dans le `xml-stylesheet` du document, ou il l’instruction de traitement vous demande le nom de fichier.  
  
 Lorsque vous modifiez un fichier XSLT, cette propriété peut être utilisée pour spécifier qu’une feuille de style différente doit être utilisée lorsque le **afficher la sortie XSLT** ou **débogage XSLT** une commande est sélectionnée. Par exemple, il se peut que vous souhaitiez utiliser cette fonction lorsque vous modifiez une feuille de style incluse dans une feuille de style parente.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)   
 [Composants de l’éditeur XML](../xml-tools/xml-editor-components.md)



