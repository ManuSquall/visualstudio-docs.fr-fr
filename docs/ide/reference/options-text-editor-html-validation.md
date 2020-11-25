---
title: Options, Éditeur de texte, HTML (Web Forms), Validation
description: Découvrez comment utiliser la page validation de la section HTML pour définir les préférences quant à la façon dont l’éditeur HTML vérifie la syntaxe du balisage HTML dans votre document.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b65edc2b6c48bc76075e909d0f9bd1341a1b6dd8
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040561"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Options, Éditeur de texte, HTML (Web Forms), Validation

Utilisez la page d’options **Validation** pour définir les préférences quant à la vérification de la syntaxe du balisage HTML de votre document par l’éditeur HTML. Pour accéder à cette page, dans la barre de menus, choisissez **Outils**  >  **options**, puis développez validation HTML de l' **éditeur**  >  **de texte (Web Forms)**  >  **Validation**.

## <a name="validation"></a>Validation

- **Utiliser un doctype pour la détection du schéma de validation**

   Un schéma détermine les éléments, attributs et la mise en majuscules valides de ce schéma. Il détermine également les balises et les attributs qui sont disponibles dans IntelliSense.

   Sélectionnez cette option si vous souhaitez que Visual Studio utilise le contenu de la déclaration **<!DOCTYPE>** et de l’élément **html** de la page pour déterminer le schéma. Par exemple, si vous sélectionnez cette option et que la page a la déclaration `<!DOCTYPE html>`, Visual Studio utilise le schéma HTML5. En revanche, si la balise **html** a un attribut **xmlns**, tel que `<html xmlns="http://www.w3.org/1999/xhtml">`, Visual Studio utilise le schéma XHTML5.

- **Cible lorsqu’aucun doctype n’est trouvé**

   Choisissez le schéma par rapport auquel effectuer une validation quand il n’y a aucune déclaration **<!DOCTYPE>** dans la page.

  - **Afficher les erreurs**

     Cochez cette case pour activer la validation. Si la case n’est pas cochée, l’éditeur ne marque pas les erreurs de validation.

     Les autres cases à cocher vous permettent de régler la validation avec précision en spécifiant les types d’erreurs spécifiques devant être marqués par l’éditeur.

     > [!NOTE]
     > Certains schémas n'offrent pas la possibilité de marquer des types d'erreurs individuels. Par exemple, si vous sélectionnez le schéma cible **XHTML 1.1**, toutes les cases sont décochées. Dans ce cas, tous les types d’erreurs sont marqués.

## <a name="see-also"></a>Voir aussi

- [Général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
