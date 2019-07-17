---
title: Définition d’une Image d’arrière-plan sur un diagramme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 28e2358b92080bd56cfda9d395f87e5c188da221
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189403"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Définition d'une image d'arrière-plan dans un schéma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le Kit de développement logiciel (SDK) de visualisation et de modélisation de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez définir l'image d'arrière-plan d'un concepteur généré à l'aide de code personnalisé.  
  
## <a name="setting-the-background-image"></a>Définition de l'image d'arrière-plan  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Pour définir une image d'arrière-plan pour un concepteur généré  
  
1. Copiez le fichier image que vous souhaitez utiliser comme arrière-plan du diagramme dans le répertoire Dsl\Resources du projet actif.  
  
2. Dans **l’Explorateur de solutions**, cliquez sur le dossier Dsl\Resources, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
3. Dans le **ajouter un élément existant** boîte de dialogue, accédez au dossier Dsl\Resources.  
  
4. Dans le **types de fichiers** , cliquez sur **fichiers Image**.  
  
5. Cliquez sur le fichier image que vous avez copiée dans le répertoire, puis cliquez sur **ajouter**.  
  
6. Cliquez sur Dsl, puis cliquez sur **propriétés** pour ouvrir les propriétés du projet Dsl.  
  
7. Sur le **ressources** sous l’onglet **ce projet ne contient pas un fichier de ressources par défaut. Cliquez ici pour en créer un.**  
  
8. Ajoutez le fichier image au fichier de ressources en faisant glisser l’image à partir de **l’Explorateur de solutions** dans la fenêtre de ressources.  
  
9. Ouvrez le menu fichier, puis cliquez sur l'option d'enregistrement des propriétés du projet.  
  
10. Vérifiez que le fichier Dsl\Properties\Resources.resx existe et que le fichier Resources.Designer.cs se trouve en dessous.  
  
11. Si Resources.Designer.cs est manquant, cliquez sur le fichier Resources.resx dans **l’Explorateur de solutions**.  
  
12. Dans la fenêtre **Propriétés** , définissez la propriété `Custom Tool` sur `ResXFileCodeGenerator`.  
  
13. Dans **l’Explorateur de solutions**, cliquez sur le projet Dsl, pointez sur **ajouter**, puis cliquez sur **nouveau dossier**.  
  
14. Nommez le dossier **personnalisé**.  
  
15. Cliquez sur le dossier Custom, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
16. Dans le **ajouter un nouvel élément** boîte de dialogue le **modèles** , cliquez sur **fichier de Code**.  
  
17. Dans le **nom** , tapez `BackgroundImage.cs`, puis cliquez sur **ajouter**.  
  
18. Copiez le code suivant dans le fichier BackgroundImage.cs, en ajustant l'espace de noms, le nom de la classe de diagramme et le nom de la ressource de fichier image.  
  
     Remplacez « MyDiagramClass » par le nom de la classe de diagramme partielle définie dans Dsl\GeneratedCode\Diagrams.cs. Vous pouvez aussi récupérer l'espace de noms correct à partir du fichier Dsl\GeneratedCode\Diagrams.cs.  
  
    ```  
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
 [Définition de formes et connecteurs](../modeling/defining-shapes-and-connectors.md)   
 [Personnalisation des champs de texte et Image](../modeling/customizing-text-and-image-fields.md)   
 [Navigation et mise à jour d’un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)
