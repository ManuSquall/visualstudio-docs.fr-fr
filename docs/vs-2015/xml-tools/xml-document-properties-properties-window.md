---
title: Propriétés des documents XML, fenêtre Propriétés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669520"
---
# <a name="xml-document-properties-properties-window"></a>Propriétés des documents XML, fenêtre Propriétés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre **Propriétés** fournit des informations de base sur le document qui est actif dans l’éditeur XML. Les propriétés disponibles varient selon le type de document XML actif.

> [!NOTE]
> Toutes les propriétés des documents XML sont enregistrées dans la solution. Vous ne devez donc pas réentrer ces valeurs la prochaine fois que vous ouvrez la solution.

 **Encodage** Encodage de caractères pour le fichier. La modification de cette propriété entraîne la modification de l'attribut d'encodage dans la déclaration XML et vice versa. Le nouvel encodage permet de coder le fichier lors de son enregistrement.

 **Entrée** Document d’entrée associé à la feuille de style XSLT. Elle est utilisée par la commande de **sortie ShowXSLT** . Un document peut être sélectionné à l’aide du bouton de navigation (**...**).

 Cette propriété n'est visible que lorsqu'un fichier XSLT est actif dans la fenêtre de l'éditeur.

 **Sortie** Fichier généré lors de la transformation d’un document XML.

 Si aucun fichier n’est spécifié, un nom de fichier par défaut est généré d’après l’attribut `method` de l’élément `xsl:output`, qui détermine l’extension du fichier. Le fichier par défaut se situe dans le répertoire temporaire de l'utilisateur actuel.

 **Schémas** Schémas à utiliser pour la validation. Le bouton ouvre la boîte de dialogue **schémas XSD** , qui peut être utilisée pour sélectionner les schémas à utiliser.

 Il permet également d’entrer le chemin des schémas. Si plusieurs schémas sont spécifiés, le chemin de chacun doit être placé entre des guillemets doubles.

 **Feuille de style** Fichier XSLT utilisé pour transformer le document lorsque la commande Afficher la **sortie XSLT** est utilisée. Si ce champ est vide lorsque la commande **afficher la sortie XSLT** est utilisée, l’éditeur utilise la valeur fournie dans l' `xml-stylesheet` instruction de traitement du document ou il vous invite à entrer le nom de fichier.

 Lorsque vous modifiez un fichier XSLT, cette propriété peut être utilisée pour spécifier qu’une autre feuille de style doit être utilisée lorsque la commande **afficher la sortie XSLT** ou **Déboguer XSLT** est sélectionnée. Par exemple, il se peut que vous souhaitiez utiliser cette fonction lorsque vous modifiez une feuille de style incluse dans une feuille de style parente.

## <a name="see-also"></a>Voir aussi
 Éditeur [XML](../xml-tools/xml-editor.md) , composants de l' [éditeur XML](../xml-tools/xml-editor-components.md)
