---
title: Options, Éditeur de texte, HTML (Web Forms), Mise en forme
description: Découvrez comment utiliser la page mise en forme dans la section HTML pour définir des options de projet HTML pour la mise en forme du code dans l’éditeur de code.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd8d7e6bd81e32858f990c70bbcdf0bf00049867
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943833"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Options, Éditeur de texte, HTML (Web Forms), Mise en forme

Utilisez la page d’options **Mise en forme** afin de définir les options de mise en forme du code dans l’éditeur de code pour les projets HTML. Pour accéder à cette page, dans la barre de menus, choisissez **Outils**  >  **options**, puis   >  mise en forme éditeur de texte **HTML (Web Forms)**  >  .

## <a name="capitalization"></a>Mise en majuscules

Lorsque ces options sont sélectionnées, le mode Source et les éditeurs XML appliquent une mise en forme de la casse par défaut aux noms d'éléments et d'attributs lorsque les éléments sont créés pour la première fois et pendant la mise en forme automatique. Les paramètres **Appliquer la mise en forme automatique** déterminent le moment où intervient la remise en forme automatique.

> [!WARNING]
> XML respecte la casse. La définition d'une casse par défaut peut avoir des répercussions sur les analyseurs XML.

### <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

**Balise Serveur, Attributs serveur**

Ces options déterminent la mise en majuscules du balisage des contrôles serveur web.

|Option|Résultats|
|---------------------------------|------------------------------|
|**Tel qu’entré**|La casse de l’élément est exactement celle que vous entrez.|
|**Majuscules**|Les noms d’éléments sont remis en forme pour être convertis en majuscules.|
|**Minuscules**|Les noms d’éléments sont remis en forme pour être convertis en minuscules.|
|**Définition d’assembly**|La casse de l’élément dépend de la manière dont l’élément est défini dans le type de classe correspondant.|

**Balise cliente, Attributs clients**

Ces options indiquent si la mise en forme automatique convertit les noms de propriétés et d’attributs HTML en majuscules ou en minuscules, ou si elle les conserve tels qu’ils ont été entrés.

|Option|Résultats|
|---------------------------------|------------------------------|
|**Tel qu’entré**|La casse de l’attribut est exactement celle que vous entrez.|
|**Majuscules**|Les noms d'attributs sont remis en forme pour être convertis en majuscules.|
|**Minuscules**|Les noms d'attributs sont remis en forme pour être convertis en minuscules.|

## <a name="automatic-formatting-options"></a>Options de mise en forme automatique

Ces options font en sorte que l’éditeur du mode Source ajoute ou supprime des sauts de ligne physiques pendant la mise en forme automatique. Vous pouvez également spécifier si l’éditeur ajoute des guillemets autour des attributs.

> [!NOTE]
> Ces paramètres ne modifient pas les espaces blancs à l'intérieur du balisage XML.

### <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Insérer des guillemets de valeur d’attribut lors de la saisie**

   Lorsque cette option est sélectionnée, l’éditeur insère automatiquement des guillemets autour des attributs à mesure que vous tapez (par exemple : ID = "Select1"). Désactivez cette option si vous préférez insérer manuellement des guillemets dans votre balisage.

   > [!NOTE]
   > Que cette option soit sélectionnée ou non, tous les guillemets existants dans votre balise sont conservés ; les guillemets ne sont jamais supprimés.

- **Insérer des guillemets de valeur d’attribut lors de la mise en forme**

   Lorsque cette option est sélectionnée, la mise en forme automatique ajoute des guillemets autour des valeurs d’attribut (par exemple : ID = "Select1").

   > [!NOTE]
   > Que cette option soit sélectionnée ou non, tous les guillemets existant dans votre balisage sont conservés.

- **Insérer automatiquement la balise de fin**

   Lorsque cette option est sélectionnée, l’éditeur crée automatiquement une balise de fermeture (par exemple, **\</b>** ) quand vous fermez la balise d’ouverture.

## <a name="tag-wrapping"></a>Balise de renvoi à la ligne

Ces options déterminent si l’éditeur scinde les balises en plusieurs lignes si elles dépassent une certaine longueur.

### <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Renvoyer les balises à la ligne au-delà de la longueur spécifiée**

   Quand cette option est sélectionnée, l’éditeur scinde les balises sur les lignes si elles dépassent la longueur que vous avez spécifiée dans la zone de texte **Longueur**. Cette action se produit uniquement lors de la mise en forme de la balise, et non quand vous entrez une nouvelle balise.

   > [!NOTE]
   > La valeur que vous spécifiez est utilisée comme une valeur minimale. L'éditeur ne scinde pas les attributs individuels.

- **Durée**

   Spécifie le nombre de caractères qui peuvent s'afficher dans une ligne avant de passer à la ligne suivante. Cette zone d’entrée est déactivée sauf si la case **Renvoyer les balises à la ligne au-delà de la longueur spécifiée** est cochée.

- **Options spécifiques pour les balises**

   Affiche la boîte de dialogue **Options spécifiques pour les balises**, qui vous permet de définir des options de mise en forme des balises individuelles ou des groupes de balises.

## <a name="see-also"></a>Voir aussi

- [Général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
