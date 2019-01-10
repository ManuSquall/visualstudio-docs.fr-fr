---
title: Options, Éditeur de texte, XML, Divers
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 85f37f4266f4c05d4de016caa07e8cc6e3cf43a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905622"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Options, Éditeur de texte, XML, Divers

Utilisez la page de propriétés **Divers** pour modifier les paramètres de complétion automatique et de schéma pour l’éditeur XML. Pour ouvrir la boîte de dialogue **Options**, cliquez sur le menu **Outils**, puis sur **Options**. Pour accéder à la page de propriétés **Divers**, développez le nœud **Éditeur de texte** > **XML** > **Divers**.

## <a name="auto-insert"></a>Insertion automatique

**Balises de fermeture**

L’éditeur de texte ajoute des balises de fermeture lors de la création des éléments XML. Si une balise de début d’un élément est sélectionnée, l’éditeur insère la balise de fermeture correspondante, avec un préfixe d’espace de noms correspondant. Elle est activée par défaut.

**Guillemets d’attribut**

Quand vous créez des attributs XML, l’éditeur insère les caractères `="` et `"`, et place le caret (**^**) à l’intérieur des guillemets doubles. Elle est activée par défaut.

**Déclarations d’espaces de noms**

L'éditeur insère automatiquement des déclarations d'espaces de noms chaque fois qu'elles sont nécessaires. Elle est activée par défaut.

**Autre balisage (commentaires, CDATA)**

Les commentaires, CDATA, DOCTYPE, les instructions de traitement et les autres éléments de balisages sont complétés automatiquement. Elle est activée par défaut.

## <a name="network"></a>Réseau

**Télécharger automatiquement les DTD et les schémas**

Les schémas et les DTD (définitions de type de document) sont automatiquement téléchargés à partir d'emplacements HTTP. Cette fonctionnalité utilise System.Net avec la détection automatique de serveur proxy activée. Elle est activée par défaut.

## <a name="outlining"></a>mode Plan

**Passer en mode Plan à l’ouverture des fichiers**

Active la fonctionnalité mode plan à l’ouverture d’un fichier. Elle est activée par défaut.

## <a name="caching"></a>Mise en cache

**Schémas**

Spécifie l'emplacement du cache de schéma. Le bouton Parcourir (...) permet d’ouvrir l’emplacement du cache de schéma actuel dans une nouvelle fenêtre. L’emplacement par défaut est *\<répertoire d’installation de Management Studio>* \Xml\Schemas.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer une documentation XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Génération de code](../code-generation-in-visual-studio.md)