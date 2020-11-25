---
title: Options, Éditeur de texte, XML, Divers
description: Découvrez comment utiliser la page divers dans la section XAML pour modifier les paramètres de saisie semi-automatique et de schéma de l’éditeur XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a02a2a133031661ecbf9c3719f3b1993f3b20b5b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040118"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Options, Éditeur de texte, XML, Divers

Utilisez la page d’options **Divers** pour modifier les paramètres de saisie semi-automatique et de schéma pour l’éditeur XML. Pour accéder aux diverses options XML, choisissez **Outils**  >  **options**  >  **éditeur de texte**  >  **XML**, puis choisissez **divers**.

## <a name="auto-insert"></a>Insertion automatique

**Balises de fermeture**

L’éditeur de texte ajoute des balises de fermeture lors de la création des éléments XML. Si la balise de début d'un élément est sélectionnée, l'Éditeur insère la balise de fin correspondante avec un préfixe d'espace de noms équivalent. Cette case à cocher est activée par défaut.

**Guillemets d'attribut**

Lors de la création d’attributs XML, l’éditeur insère `="` les `"` caractères et et positionne le signe insertion ( **^** ) à l’intérieur des guillemets. Cette case à cocher est activée par défaut.

**Déclarations d'espace de noms**

L'Éditeur insère automatiquement les déclarations d'espace de noms là où elles sont requises. Cette case à cocher est activée par défaut.

**Autre balisage (Commentaires, CDATA)**

Les éléments CDATA, DOCTYPE, les commentaires, les instructions de traitement et autre balisage sont entrés automatiquement. Cette case à cocher est activée par défaut.

## <a name="network"></a>Réseau

**Télécharger automatiquement les DTD et les schémas**

Les schémas et les définitions de type de document (DTD) sont automatiquement téléchargés à partir d'emplacements HTTP. Cette fonctionnalité utilise System.Net avec détection de serveur de proxy automatique. Cette case à cocher est activée par défaut.

## <a name="outlining"></a>mode Plan

**Passer en mode Plan à l'ouverture des fichiers**

Active la fonctionnalité mode Plan lorsqu'un fichier est ouvert. Cette case à cocher est activée par défaut.

## <a name="caching"></a>Mise en cache

**Schémas**

Indique l'emplacement du cache des schémas. Le bouton **Parcourir** permet d’ouvrir l’emplacement du cache de schéma actuel dans une nouvelle fenêtre. L’emplacement par défaut est *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Voir aussi

- [Options XML - Mise en forme](options-text-editor-xml-formatting.md)
- [Outils XML dans Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
