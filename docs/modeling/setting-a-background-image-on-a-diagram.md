---
title: Définition d'une image d'arrière-plan dans un schéma
description: Découvrez que dans le kit de développement logiciel (SDK) de visualisation et de modélisation de Visual Studio, vous pouvez définir l’image d’arrière-plan d’un concepteur généré à l’aide de code personnalisé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9304117932b92408f12a23747253de66dfd767d1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385667"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Définition d'une image d'arrière-plan dans un schéma
Dans le kit de développement logiciel (SDK) de visualisation et de modélisation Visual Studio, vous pouvez définir l’image d’arrière-plan d’un concepteur généré à l’aide de code personnalisé.

## <a name="setting-the-background-image"></a>Définir l'image d'arrière-plan

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Pour définir une image d'arrière-plan pour un concepteur généré

1. Copiez le fichier image que vous souhaitez utiliser comme arrière-plan du diagramme dans le répertoire Dsl\Resources du projet actif.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier Dsl\Resources, pointez sur **Ajouter**, puis cliquez sur **élément existant**.

3. Dans la boîte de dialogue **Ajouter un élément existant** , accédez au dossier Dsl\Resources.

4. Dans la liste **types de fichiers** , cliquez sur **fichiers image**.

5. Cliquez sur le fichier image que vous avez copié dans le répertoire, puis cliquez sur **Ajouter**.

6. Cliquez avec le bouton droit sur DSL, puis cliquez sur **Propriétés** pour ouvrir les propriétés du projet DSL.

7. Sous l’onglet **ressources** , cliquez sur **ce projet ne contient pas de fichier de ressources par défaut. Cliquez ici pour en créer un.**

8. Ajoutez le fichier image au fichier de ressources en faisant glisser l’image de **Explorateur de solutions** vers la fenêtre ressources.

9. Ouvrez le menu fichier, puis cliquez sur l'option d'enregistrement des propriétés du projet.

10. Vérifiez que le fichier Dsl\Properties\Resources.resx existe et que le fichier Resources.Designer.cs se trouve en dessous.

11. Si Resources. Designer. cs est manquant, cliquez sur le fichier Resources. resx dans **Explorateur de solutions**.

12. Dans la fenêtre **Propriétés** , définissez la propriété `Custom Tool` sur `ResXFileCodeGenerator`.

13. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet DSL, pointez sur **Ajouter**, puis cliquez sur **nouveau dossier**.

14. Nommez le dossier **personnalisé**.

15. Cliquez avec le bouton droit sur le dossier personnalisé, pointez sur **Ajouter**, puis cliquez sur **nouvel élément**.

16. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans la liste **modèles** , cliquez sur **fichier de code**.

17. Dans la zone **nom** , tapez `BackgroundImage.cs` , puis cliquez sur **Ajouter**.

18. Copiez le code suivant dans le fichier BackgroundImage.cs, en ajustant l'espace de noms, le nom de la classe de diagramme et le nom de la ressource de fichier image.

     Remplacez « MyDiagramClass » par le nom de la classe de diagramme partielle définie dans Dsl\GeneratedCode\Diagrams.cs. Vous pouvez aussi récupérer l'espace de noms correct à partir du fichier Dsl\GeneratedCode\Diagrams.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Pour plus d’informations sur la personnalisation du modèle à l’aide du code de programme, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Voir aussi

- [Définition de formes et de connecteurs](../modeling/defining-shapes-and-connectors.md)
- [Personnalisation des champs de texte et d'image](../modeling/customizing-text-and-image-fields.md)
- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
