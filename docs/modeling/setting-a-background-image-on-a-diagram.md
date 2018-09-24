---
title: Définition d'une image d'arrière-plan dans un schéma
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3086f6f99497789eace3ff999a8fa0693b497324
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567362"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Définition d'une image d'arrière-plan dans un schéma
Dans le Kit de développement logiciel (SDK) de visualisation et de modélisation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez définir l'image d'arrière-plan d'un concepteur généré à l'aide de code personnalisé.

## <a name="setting-the-background-image"></a>Définition de l'image d'arrière-plan

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Pour définir une image d'arrière-plan pour un concepteur généré

1.  Copiez le fichier image que vous souhaitez utiliser comme arrière-plan du diagramme dans le répertoire Dsl\Resources du projet actif.

2.  Dans **l’Explorateur de solutions**, cliquez sur le dossier Dsl\Resources, pointez sur **ajouter**, puis cliquez sur **élément existant**.

3.  Dans le **ajouter un élément existant** boîte de dialogue, accédez au dossier Dsl\Resources.

4.  Dans le **types de fichiers** , cliquez sur **fichiers Image**.

5.  Cliquez sur le fichier image que vous avez copiée dans le répertoire, puis cliquez sur **ajouter**.

6.  Cliquez sur Dsl, puis cliquez sur **propriétés** pour ouvrir les propriétés du projet Dsl.

7.  Sur le **ressources** sous l’onglet **ce projet ne contient pas un fichier de ressources par défaut. Cliquez ici pour en créer un.**

8.  Ajoutez le fichier image au fichier de ressources en faisant glisser l’image à partir de **l’Explorateur de solutions** dans la fenêtre de ressources.

9. Ouvrez le menu fichier, puis cliquez sur l'option d'enregistrement des propriétés du projet.

10. Vérifiez que le fichier Dsl\Properties\Resources.resx existe et que le fichier Resources.Designer.cs se trouve en dessous.

11. Si Resources.Designer.cs est manquant, cliquez sur le fichier Resources.resx dans **l’Explorateur de solutions**.

12. Dans le **propriétés** fenêtre, définissez la `Custom Tool` propriété `ResXFileCodeGenerator`.

13. Dans **l’Explorateur de solutions**, cliquez sur le projet Dsl, pointez sur **ajouter**, puis cliquez sur **nouveau dossier**.

14. Nommez le dossier **personnalisé**.

15. Cliquez sur le dossier Custom, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.

16. Dans le **ajouter un nouvel élément** boîte de dialogue le **modèles** , cliquez sur **fichier de Code**.

17. Dans le **nom** , tapez `BackgroundImage.cs`, puis cliquez sur **ajouter**.

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

     Pour plus d’informations sur la personnalisation du modèle avec le code de programme, consultez [navigation et la mise à jour un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Voir aussi

- [Définition de formes et de connecteurs](../modeling/defining-shapes-and-connectors.md)
- [Personnalisation des champs de texte et d’image](../modeling/customizing-text-and-image-fields.md)
- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
