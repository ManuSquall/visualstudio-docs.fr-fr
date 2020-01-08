---
title: Options, Éditeur de texte, XML, Divers
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dd468945b1ab9ac83b219b9c8c396f017065e2be
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568124"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Options, Éditeur de texte, XML, Divers

Utilisez la page d’options **Divers** pour modifier les paramètres de saisie semi-automatique et de schéma pour l’éditeur XML. Pour accéder aux options XML diverses, choisissez **Outils** > **Options** > **Éditeur de texte** > **XML**, puis **Divers**.

## <a name="auto-insert"></a>Insertion automatique

**Balises de fermeture**

L’éditeur de texte ajoute des balises de fermeture lors de la création des éléments XML. Si une balise de début d’un élément est sélectionnée, l’éditeur insère la balise de fermeture correspondante, avec un préfixe d’espace de noms correspondant. Cette case à cocher est sélectionnée par défaut.

**Guillemets d’attribut**

Quand vous créez des attributs XML, l’éditeur insère les caractères `="` et `"`, et place le caret ( **^** ) à l’intérieur des guillemets doubles. Cette case à cocher est sélectionnée par défaut.

**Déclarations d’espaces de noms**

L'éditeur insère automatiquement des déclarations d'espaces de noms chaque fois qu'elles sont nécessaires. Cette case à cocher est sélectionnée par défaut.

**Autre balisage (commentaires, CDATA)**

Les commentaires, CDATA, DOCTYPE, les instructions de traitement et les autres éléments de balisages sont complétés automatiquement. Cette case à cocher est sélectionnée par défaut.

## <a name="network"></a>Réseau

**Télécharger automatiquement les DTD et les schémas**

Les schémas et les DTD (définitions de type de document) sont automatiquement téléchargés à partir d'emplacements HTTP. Cette fonctionnalité utilise System.Net avec la détection automatique de serveur proxy activée. Cette case à cocher est sélectionnée par défaut.

## <a name="outlining"></a>mode Plan

**Passer en mode Plan à l’ouverture des fichiers**

Active le mode plan à l'ouverture d'un fichier. Cette case à cocher est sélectionnée par défaut.

## <a name="caching"></a>Mise en cache

**Schémas**

Spécifie l'emplacement du cache de schéma. Le bouton **Parcourir** permet d’ouvrir l’emplacement du cache de schéma actuel dans une nouvelle fenêtre. L’emplacement par défaut est *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Voir aussi

- [Options XML - Mise en forme](options-text-editor-xml-formatting.md)
- [Outils XML dans Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
