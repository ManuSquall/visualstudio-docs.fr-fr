---
title: "D&#233;finition d&#39;une image d&#39;arri&#232;re-plan dans un sch&#233;ma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# D&#233;finition d&#39;une image d&#39;arri&#232;re-plan dans un sch&#233;ma
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le Kit de développement logiciel \(SDK\) de visualisation et de modélisation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez définir l'image d'arrière\-plan d'un concepteur généré à l'aide de code personnalisé.  
  
## Définition de l'image d'arrière\-plan  
  
#### Pour définir une image d'arrière\-plan pour un concepteur généré  
  
1.  Copiez le fichier image que vous souhaitez utiliser comme arrière\-plan du diagramme dans le répertoire Dsl\\Resources du projet actif.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le dossier Dsl\\Resources, pointez sur **Ajouter**, puis cliquez sur **Élément existant**.  
  
3.  Dans la boîte de dialogue **Ajouter un élément existant**, accédez au dossier Dsl\\Resources.  
  
4.  Dans la liste **Types de fichiers**, cliquez sur **Fichiers image**.  
  
5.  Cliquez sur le fichier image que vous avez copié dans le répertoire, puis cliquez sur **Ajouter**.  
  
6.  Cliquez avec le bouton droit sur Dsl, puis cliquez sur **Propriétés** pour ouvrir les propriétés du projet Dsl.  
  
7.  Sous l'onglet **Ressources**, cliquez sur **Ce projet ne contient pas de fichier de ressources par défaut. Cliquez ici pour en créer un.**  
  
8.  Ajoutez le fichier image au fichier de ressources en faisant glisser l'image de l'**Explorateur de solutions** vers la fenêtre de ressources.  
  
9. Ouvrez le menu fichier, puis cliquez sur l'option d'enregistrement des propriétés du projet.  
  
10. Vérifiez que le fichier Dsl\\Properties\\Resources.resx existe et que le fichier Resources.Designer.cs se trouve en dessous.  
  
11. Si Resources.Designer.cs est absent, cliquez sur le fichier Resources.resx dans l'**Explorateur de ressources**.  
  
12. Dans la fenêtre **Propriétés**, affectez la valeur `ResXFileCodeGenerator` à la propriété `Custom Tool`.  
  
13. Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet Dsl, pointez sur **Ajouter**, puis cliquez sur **Nouveau dossier**.  
  
14. Nommez le dossier Custom.  
  
15. Cliquez avec le bouton droit sur le dossier Custom, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.  
  
16. Dans la boîte de dialogue **Ajouter un nouveau éléments**, dans la liste **Modèles**, cliquez sur **Fichier de code**.  
  
17. Dans la zone **Nom**, tapez `BackgroundImage.cs`, puis cliquez sur **Ajouter**.  
  
18. Copiez le code suivant dans le fichier BackgroundImage.cs, en ajustant l'espace de noms, le nom de la classe de diagramme et le nom de la ressource de fichier image.  
  
     Remplacez « MyDiagramClass » par le nom de la classe de diagramme partielle définie dans Dsl\\GeneratedCode\\Diagrams.cs.  Vous pouvez aussi récupérer l'espace de noms correct à partir du fichier Dsl\\GeneratedCode\\Diagrams.cs.  
  
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
  
     Pour plus d'informations sur la personnalisation du modèle avec du code de programme, consultez [Navigation et mise à jour d'un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## Voir aussi  
 [Définition de formes et de connecteurs](../modeling/defining-shapes-and-connectors.md)   
 [Personnalisation des champs de texte et Image](../modeling/customizing-text-and-image-fields.md)   
 [Navigation et mise à jour d'un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Écrire du Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)