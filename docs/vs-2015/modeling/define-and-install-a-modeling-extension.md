---
title: Définir et installer une extension de modélisation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cf370b4ca0e0a4d14c482c6ece46b79d2d224d34
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049735"
---
# <a name="define-and-install-a-modeling-extension"></a>Définir et installer une extension de modélisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez définir des extensions de diagrammes de modélisation. De cette manière, vous pouvez adapter les diagrammes et les modèles à vos besoins. Par exemple, vous pouvez définir des commandes de menu, des profils UML, des contraintes de validation et des éléments de boîte à outils. Vous pouvez définir plusieurs composants dans une même extension. Vous pouvez aussi distribuer ces extensions à d’autres utilisateurs de Visual Studio sous la forme d’une [Extension d’intégration Visual Studio (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780). Vous pouvez créer une extension VSIX à l’aide d’un projet VSIX dans Visual Studio.  
  
## <a name="requirements"></a>Configuration requise  
 Consultez [Spécifications](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-modeling-extension-solution"></a>Création d’une solution d’extension de modélisation  
 Pour définir une extension de modélisation, vous devez créer une solution contenant ces projets :  
  
- Un projet d’Extension d’intégration [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). Cela génère un fichier qui agit comme un programme d’installation pour les composants de votre extension.  
  
- Un projet de bibliothèque de classes, nécessaire pour les composants qui incluent du code de programme.  
  
  Si vous souhaitez créer une extension qui comporte plusieurs composants, vous pouvez les développer dans une solution unique. Un seul projet VSIX suffit.  
  
  Vous pouvez ajouter des composants qui ne nécessitent pas de code, comme les éléments de boîte à outils personnalisés et les profils UML personnalisés, directement au projet VSIX sans utiliser de projets de bibliothèque de classes distincts. Il est plus facile de définir les composants qui nécessitent du code de programme dans un projet de bibliothèque de classes distinct. Il s’agit de composants tels que les gestionnaires de mouvements, les commandes de menu et le code de validation.  
  
#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Pour créer un projet de bibliothèque de classes pour des commandes de menu, des gestionnaires de mouvements ou la validation  
  
1. Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**.  
  
2. Sous **Modèles installés**, sélectionnez **Visual C#** ou **Visual Basic**, puis choisissez **Bibliothèque de classes**.  
  
#### <a name="to-create-a-vsix-project"></a>Pour créer un projet VSIX  
  
1. Si vous créez un composant avec du code, il est plus facile de commencer par créer le projet de bibliothèque de classes. Vous ajouterez votre code à ce projet.  
  
2. Créez un projet VSIX.  
  
    1. Dans l’ **Explorateur de solutions**, dans le menu contextuel de la solution, choisissez **Ajouter**, puis **Nouveau projet**.  
  
    2. Sous **Modèles installés**, développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Extensibilité**. Dans la colonne du milieu, choisissez **Projet VSIX**.  
  
3. Définissez le projet VSIX comme projet de démarrage de la solution.  
  
    - Dans l’Explorateur de solutions, dans le menu contextuel du projet VSIX, choisissez **Définir comme projet de démarrage**.  
  
4. Ouvrez **source.extension.vsixmanifest**. Le fichier s’ouvre dans l’éditeur de manifeste.  
  
5. Sous l’onglet **Métadonnées** , définissez les champs de nom et de description de l’extension VSIX.  
  
6. Sous l’onglet **Cibles d’installation** , choisissez **Nom** et définissez les versions de Visual Studio comme cibles.  
  
7. Sous l’onglet **Composants** , ajoutez vos composants à l’extension Visual Studio.  
  
    1. Choisissez **Nouveau**.  
  
    2. Pour un composant avec du code, définissez les champs suivants dans la boîte de dialogue **Ajouter un nouveau composant** :  
  
        |||  
        |-|-|  
        |**Type** =|**Microsoft.VisualStudio.MefComponent**|  
        |**Source** =|**Un projet dans la solution actuelle**|  
        |**projet** =|*Votre projet de bibliothèque de classes*|  
        |**Incorporer dans ce dossier** =|*(vide)*|  
  
         Pour les autres types de composants, consultez les liens dans la section suivante.  
  
## <a name="developing-the-component"></a>Développement du composant  
 Pour chaque composant tel qu’un gestionnaire de mouvements ou une commande de menu, vous devez définir un gestionnaire distinct. Vous pouvez placer plusieurs gestionnaires dans le même projet de bibliothèque de classes. Le tableau suivant résume les différents types de gestionnaires.  
  
|Type d’extension|Rubrique|Comment chaque composant est généralement déclaré|  
|--------------------|-----------|----------------------------------------------|  
|Commande de menu|[Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|  
|Glisser-déplacer ou double-clic|[Définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|  
|Contrainte de validation|[Définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|  
|Gestionnaire d’événements de lien d’élément de travail|[Définir un gestionnaire de liens d’éléments de travail](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|  
|Profil UML|[Définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md)|(À définir)|  
|Élément de boîte à outils|[Définir un élément de boîte à outils de modélisation personnalisé](../modeling/define-a-custom-modeling-toolbox-item.md)|(À définir)|  
  
## <a name="running-an-extension-during-its-development"></a>Exécution d’une extension durant son développement  
  
#### <a name="to-run-an-extension-during-its-development"></a>Pour exécuter une extension durant son développement  
  
1. Dans le menu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **de** , choisissez **Start deging**.  
  
     Le projet est généré et une nouvelle instance de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] démarre en mode expérimental.  
  
    - Vous pouvez également choisir **Exécuter sans débogage**. Cela réduit le temps nécessaire au démarrage du programme.  
  
2. Créez ou ouvrez un projet de modélisation dans l’instance expérimentale de Visual Studio et créez ou ouvrez un diagramme.  
  
     Votre extension se charge et s’exécute.  
  
3. Si vous avez utilisé l’option **Exécuter sans débogage** mais que vous souhaitez utiliser le débogueur, revenez à l’instance principale de Visual Studio. Dans le menu **Déboguer** , cliquez sur **Attacher au processus**. Dans la boîte de dialogue, sélectionnez l’instance expérimentale de Visual Studio, dont le nom de programme est **devenv**.  
  
## <a name="Installing"></a> Installation et désinstallation d’une extension  
 Procédez comme suit pour exécuter votre extension dans l’instance principale de Visual Studio sur votre ordinateur ou sur d’autres ordinateurs.  
  
1. Sur votre ordinateur, recherchez le fichier **.vsix** généré par votre projet d’extension.  
  
    1. Dans l’ **Explorateur de solutions**, dans le menu contextuel de votre projet, choisissez **Ouvrir le dossier dans l’Explorateur Windows**.  
  
    2. Recherchez le fichier **bin\\\*\\**_VotreProjet_**.vsix**  
  
2. Copiez le fichier **.vsix** sur l’ordinateur cible sur lequel vous souhaitez installer l’extension. Il peut s’agir de votre propre ordinateur ou d’un autre ordinateur.  
  
    - L’ordinateur cible doit avoir l’une des éditions de Visual Studio que vous avez spécifiées sous l’onglet **Cibles d’installation** de **source.extension.vsixmanifest**.  
  
3. Sur l’ordinateur cible, ouvrez le fichier **.vsix** , par exemple en double-cliquant dessus.  
  
     Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.  
  
4. Démarrez ou redémarrez Visual Studio.  
  
#### <a name="to-uninstall-an-extension"></a>Pour désinstaller une extension  
  
1. Dans le menu **Outils** , choisissez **Extensions et mises à jour**.  
  
2. Développez **Extensions installées**.  
  
3. Sélectionnez l’extension, puis cliquez sur **Désinstaller**.  
  
   Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier à partir de l’emplacement suivant où *% LocalAppData%* est généralement *nom_lecteur*: \Users\\*nom d’utilisateur*\AppData\Local :  
  
   *%LocalAppData%* **\Microsoft\VisualStudio\\[version]\Extensions**  
  
## <a name="see-also"></a>Voir aussi  
 [Définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Définir un personnalisé élément de boîte à outils de modélisation](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
