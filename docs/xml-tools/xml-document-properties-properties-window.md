---
title: Propriétés des documents XML, fenêtre Propriétés
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b21f4435737597136e1ac4a4dd8651decaf4c65
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592423"
---
# <a name="xml-document-properties-properties-window"></a>Propriétés de document XML, Fenêtre Propriétés

La fenêtre **Propriétés** fournit des informations de base sur le document qui est actif dans l’éditeur XML. Les propriétés disponibles varient selon le type de document XML actif.

> [!NOTE]
> Toutes les propriétés des documents XML sont enregistrées dans la solution. Vous ne devez donc pas réentrer ces valeurs la prochaine fois que vous ouvrez la solution.

**Encodage**

Encodage de caractères utilisé pour le fichier. La modification de cette propriété entraîne la modification de l'attribut d'encodage dans la déclaration XML et vice versa. Le nouvel encodage est utilisé pour encoder le fichier lorsque vous enregistrez le fichier.

**Entrée**

Document d'entrée associé à la feuille de style XSLT. Il est utilisé par les commandes de **démarrage XSLT** , par exemple, **XML** > **Démarrer XSLT sans débogage**. Un document peut être sélectionné à l’aide du bouton de navigation ( **...** ).

Cette propriété est visible uniquement lorsqu’un fichier XSLT est ouvert dans l’éditeur.

**Sortie**

Fichier généré lors de la transformation d'un document XML.

Si aucun fichier n’est spécifié, un nom de fichier par défaut est généré en fonction de l’attribut `method` sur l’élément `xsl:output`, qui détermine l’extension de fichier. Le fichier par défaut se situe dans le répertoire temporaire de l'utilisateur actuel.

**Schémas**

Schémas utilisés pour la validation. Le bouton ouvre la boîte de dialogue **schémas XSD** , qui peut être utilisée pour sélectionner les schémas à utiliser.

Il permet également d’entrer le chemin des schémas. Si plusieurs schémas sont spécifiés, le chemin de chacun doit être placé entre des guillemets doubles.

**Feuille**

Fichier XSLT utilisé pour transformer le document lors de l’utilisation des commandes **Démarrer le débogage XSLT** et **Démarrer XSLT sans débogage** . Si ce champ est vide, l’éditeur utilise la valeur fournie dans le `xml-stylesheet` instruction de traitement du document ou il vous invite à entrer un nom de fichier.

Lorsque vous modifiez un fichier XSLT, cette propriété peut être utilisée pour spécifier qu’une autre feuille de style doit être utilisée lorsque la commande **Démarrer le débogage XSLT** ou **Démarrer XSLT sans débogage** est sélectionnée. Par exemple, vous souhaiterez peut-être le faire lorsque vous modifiez une feuille de style qui est incluse dans une feuille de style parente.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
