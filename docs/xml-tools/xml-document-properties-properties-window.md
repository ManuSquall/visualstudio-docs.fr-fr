---
title: Propriétés des documents XML, fenêtre Propriétés
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 679ac529708a49d18025672ce8f880c4f7710471
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808130"
---
# <a name="xml-document-properties-properties-window"></a>Propriétés des documents XML, fenêtre Propriétés

Le **propriétés** fenêtre fournit des informations de base sur le document est actif dans l’éditeur XML. Les propriétés disponibles varient selon le type de document XML actif.

> [!NOTE]
> Toutes les propriétés des documents XML sont enregistrées dans la solution. Vous ne devez donc pas réentrer ces valeurs la prochaine fois que vous ouvrez la solution.

**Encodage**

Encodage de caractères utilisé pour le fichier. La modification de cette propriété entraîne la modification de l'attribut d'encodage dans la déclaration XML et vice versa. Le nouvel encodage est utilisé pour encoder le fichier lorsque vous enregistrez le fichier.

**Entrée**

Document d'entrée associé à la feuille de style XSLT. Il est utilisé par le **XSLT Démarrer** des commandes, par exemple, **XML** > **démarrer sans débogage XSLT**. Un document peut être sélectionné à l’aide de la navigation (**...** ) bouton.

Cette propriété est visible uniquement quand un fichier XSLT est ouvert dans l’éditeur.

**Sortie**

Fichier généré lors de la transformation d'un document XML.

Si un fichier n’est pas spécifié, un nom de fichier par défaut est généré en fonction de la `method` d’attribut sur le `xsl:output` élément, qui détermine l’extension de fichier. Le fichier par défaut se situe dans le répertoire temporaire de l'utilisateur actuel.

**Schémas**

Schémas utilisés pour la validation. Le bouton ouvre le **schémas XSD** boîte de dialogue, qui peut être utilisé pour sélectionner les schémas à utiliser.

Il permet également d’entrer le chemin des schémas. Si plusieurs schémas sont spécifiés, le chemin de chacun doit être placé entre des guillemets doubles.

**Feuille de style**

Le fichier XSLT utilisé pour transformer le document lorsque le **démarrer le débogage XSLT** et **démarrer sans débogage XSLT** commandes sont utilisées. Si ce champ est vide, l’éditeur utilise la valeur fournie dans le `xml-stylesheet` du document, ou l’instruction de traitement vous demande un nom de fichier.

Lorsque vous modifiez un fichier XSLT, cette propriété peut être utilisée pour spécifier qu’une feuille de style différente doit être utilisée lorsque le **démarrer le débogage XSLT** ou **démarrer sans débogage XSLT** une commande est sélectionnée. Par exemple, vous souhaiterez faire lorsque vous modifiez une feuille de style qui est incluse dans une feuille de style parente.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)