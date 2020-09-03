---
title: Divers, XML, éditeur de texte, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656237"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Divers, XML, Éditeur de texte, boîte de dialogue Options
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue permet de modifier les paramètres de saisie semi-automatique et de schéma de l'éditeur XML. Vous pouvez accéder à la boîte de dialogue **Options** à partir du menu **Outils**.

> [!NOTE]
> Ces paramètres sont disponibles lorsque vous sélectionnez le dossier **éditeur de texte** , le dossier **XML** , puis l’option **divers** dans la boîte de dialogue **options** .

## <a name="auto-insert"></a>Insertion automatique
 **Balises de fermeture** Si le paramètre de saisie semi-automatique est activé, l’éditeur ajoute automatiquement une balise de fin lorsque vous tapez un chevron droit (>) pour fermer une balise de début, si la balise n’est pas déjà fermée. Il s'agit du comportement par défaut.

 La saisie d'un élément vide ne dépend pas du paramètre de saisie semi-automatique. Vous pouvez toujours effectuer la saisie semi-automatique d'un élément vide en tapant une barre oblique inverse (/).

 **Guillemets d’attribut** Lors de la création d’attributs XML, l’éditeur insère les `=" "` caractères et place le signe insertion (^) à l’intérieur des guillemets doubles.

 Option sélectionnée par défaut.

 **Déclarations d’espaces de noms** L’éditeur insère automatiquement les déclarations d’espace de noms partout où elles sont nécessaires.

 Option sélectionnée par défaut.

 **Autre balisage (commentaires, CDATA)** Les commentaires, CDATA, DOCTYPE, les instructions de traitement et les autres balises sont terminés automatiquement.

 Option sélectionnée par défaut.

## <a name="network"></a>Réseau
 **Télécharger automatiquement les DTD et les schémas** Les schémas et les définitions de type de document (DTD) sont automatiquement téléchargés à partir d’emplacements HTTP. Cette fonctionnalité utilise System.Net avec la détection automatique de serveur proxy activée.

 Option sélectionnée par défaut.

## <a name="outlining"></a>mode Plan
 **Passer en mode plan** à l’ouverture des fichiers Active la fonctionnalité mode plan lorsqu’un fichier est ouvert.

 Option sélectionnée par défaut.

## <a name="caching"></a>Mise en cache
 **Schémas** Spécifie l’emplacement du cache de schéma. Le bouton Parcourir (**...**) ouvre la boîte de dialogue **Parcourir les répertoires** à l’emplacement actuel du cache de schéma. Vous pouvez sélectionner un autre répertoire, ou vous pouvez sélectionner un dossier dans la boîte de dialogue, cliquer avec le bouton droit, puis choisir **ouvrir** pour voir ce qui se trouve dans le répertoire.

## <a name="see-also"></a>Voir aussi
 [Propriétés de document XML, fenêtre Propriétés composants de](../xml-tools/xml-document-properties-properties-window.md) l' [éditeur XML](../xml-tools/xml-editor-components.md)
