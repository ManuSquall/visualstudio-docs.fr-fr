---
title: Options, Éditeur de texte, HTML (Web Forms), Validation
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
ms.openlocfilehash: ede4600cb1fa1df118b4635a193d8bff348d5119
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568280"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Options, Éditeur de texte, HTML (Web Forms), Validation

Utilisez la page d’options **Validation** pour définir les préférences quant à la vérification de la syntaxe du balisage HTML de votre document par l’éditeur HTML. Pour accéder à cette page, dans la barre de menus, choisissez **Outils** > **Options**, puis développez **Éditeur de texte** > **HTML (Web Forms)**  > **Validation**.

## <a name="validation"></a>Validation

- **Utiliser un doctype pour la détection du schéma de validation**

   Un schéma détermine les éléments, attributs et la mise en majuscules valides de ce schéma. Il détermine également les balises et les attributs qui sont disponibles dans IntelliSense.

   Sélectionnez cette option si vous souhaitez que Visual Studio utilise le contenu de la déclaration **<!DOCTYPE>** et de l’élément **html** de la page pour déterminer le schéma. Par exemple, si vous sélectionnez cette option et que la page a la déclaration `<!DOCTYPE html>`, Visual Studio utilise le schéma HTML5. En revanche, si la balise **html** a un attribut **xmlns**, tel que `<html>`, Visual Studio utilise le schéma XHTML5.

- **Cible lorsqu’aucun doctype n’est trouvé**

   Choisissez le schéma par rapport auquel effectuer une validation quand il n’y a aucune déclaration **<!DOCTYPE>** dans la page.

  - **Afficher les erreurs**

     Cochez cette case pour activer la validation. Si la case n’est pas cochée, l’éditeur ne marque pas les erreurs de validation.

     Les autres cases à cocher vous permettent de régler la validation avec précision en spécifiant les types d’erreurs spécifiques devant être marqués par l’éditeur.

     > [!NOTE]
     > Certains schémas n'offrent pas la possibilité de marquer des types d'erreurs individuels. Par exemple, si vous sélectionnez le schéma cible **XHTML 1.1**, toutes les cases sont décochées. Dans ce cas, tous les types d’erreurs sont marqués.

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
