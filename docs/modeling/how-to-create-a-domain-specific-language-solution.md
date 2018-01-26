---
title: "Comment : créer une Solution de langage spécifique à un domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a8b349e43f4728fee3ec676a689e6ba03cde758
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Comment : créer une solution de langage spécifique à un domaine
Un langage spécifique à un domaine (DSL) est créé à l’aide de spécialisé [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution.  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de commencer cette procédure, vous devez d’abord installer ces composants :  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>Création d’une Solution de langage spécifique à un domaine  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Pour créer une solution de langage spécifique à un domaine  
  
1.  Démarrez l’Assistant DSL.  
  
    1.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
    2.  La boîte de dialogue **Nouveau projet** s’affiche.  
  
    3.  Sous **types de projet**, développez le **autres Types de projets** nœud, puis cliquez sur **extensibilité**.  
  
    4.  Cliquez sur **Concepteur de langage spécifique à un domaine**.  
  
    5.  Dans le **nom** , tapez un nom pour la solution. Cliquez sur **OK**.  
  
         Le **Assistant Concepteur de langage spécifique à un domaine** s’affiche.  
  
        > [!NOTE]
        >  De préférence, le nom que vous tapez doit être un identificateur c# valide, car il peut être utilisé pour générer le code.  
  
     ![Boîte de dialogue DSL créer](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  Choisissez un modèle DSL.  
  
     Sur le **sélectionner les Options de langage spécifique à un domaine** page, sélectionnez un des modèles de solution telle que **langage minimale**. Choisissez un modèle qui est similaire à la DSL que vous souhaitez créer.  
  
     Pour plus d’informations sur les modèles de solution, consultez [choisir un modèle de Solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3.  Entrez une extension de nom de fichier sur le **Extension de fichier** page. Il doit être unique dans votre ordinateur, et dans tous les ordinateurs sur lesquels vous souhaitez installer le DSL. Vous devez voir le message **aucune application ou les éditeurs de Visual Studio n’utilisent cette extension**.  
  
    -   Si vous avez utilisé l’extension de nom de fichier dans DSL expérimentale précédente qui n’ont pas été entièrement installé, vous pouvez les désactiver à l’aide de la **réinitialiser l’Instance expérimentale** outil, qui se trouve dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menu du Kit de développement logiciel.  
  
    -   Si un autre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension qui utilise cette extension de fichier a été entièrement installée sur votre ordinateur, envisagez de le désinstaller. Sur le **outils** menu, cliquez sur **Gestionnaire d’extensions**.  
  
4.  Examiner et ajuster si nécessaire, les champs dans les pages restantes de l’Assistant. Lorsque vous êtes satisfait des paramètres, cliquez sur **Terminer**. Pour plus d’informations sur les paramètres, consultez [Pages de l’Assistant concepteur DSL](#settings).  
  
     L’Assistant crée une solution qui contient deux projets, qui sont nommées **Dsl** et **DslPackage**.  
  
    > [!NOTE]
    >  Si vous voyez un message qui vous n'avertit pas pour exécuter des modèles de texte à partir de sources non fiables, cliquez sur **OK**. Vous pouvez définir ce message s’affiche à nouveau.  
  
##  <a name="settings"></a>Les Pages de l’Assistant concepteur DSL  
 Vous pouvez laisser certains champs identique à leurs valeurs par défaut. Toutefois, assurez-vous que vous définissez le champ d’Extension de fichier.  
  
### <a name="solution-settings-page"></a>Page Paramètres de solution  
 **Quel est le modèle vous voulez baser votre langage spécifique à un domaine sur ?**  
 Choisissez un modèle qui est similaire à la DSL que vous souhaitez créer. Les différents modèles fournissent des points de départ pratiques. Lorsque vous sélectionnez un modèle de solution, l’Assistant affiche une description. Pour plus d’informations sur les modèles de solution, consultez [choisir un modèle de Solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **Que voulez-vous nommer votre langage spécifique à un domaine ?**  
 Par défaut, le nom de la solution. Code est généré à partir de cette valeur. Il doit être valide comme nom de classe c#.  
  
### <a name="file-extension-page"></a>Page Extension de fichier  
 **Les extensions doivent modéliser de fichiers utilisent ?**  
 Tapez une nouvelle extension de fichier.  
  
 Vérifiez que cette extension de fichier n'a pas déjà été inscrit pour une utilisation sur cet ordinateur, comme suit :  
  
 Regardez sous **autres outils et applications inscrit pour gérer cette extension**. Si vous voyez le message **aucune application ou les éditeurs de Visual Studio n’utilisent cette extension**, vous pouvez ensuite utiliser cette extension de fichier.  
  
 Si vous voyez une liste des outils ou des packages, vous devez procédez à une des opérations suivantes :  
  
-   Tapez une extension de fichier différent.  
  
     \- ou -  
  
-   Réinitialiser le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Instance expérimentale. Cela annulera toutes les DSL que vous avez déjà créé. Sur le **Démarrer** menu, cliquez sur **tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **outils**, puis **réinitialiser le Instance de Microsoft Visual Studio 2010 expérimentale**. Vous pouvez reconstruire les autres DSL que vous souhaitez utiliser à nouveau.  
  
     \- ou -  
  
-   Si un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension qui utilise cette extension de fichier a été entièrement installée sur votre ordinateur, désinstallez-la. Sur le **outils** menu, cliquez sur **Gestionnaire d’extensions**.  
  
### <a name="product-settings-page"></a>Page des paramètres de produit  
 **Quel est le nom du produit auquel appartient le nouveau langage spécifique à un domaine ?**  
 Par défaut, le nom DSL.  
  
 Cette valeur est utilisée dans l’Explorateur Windows (ou l’Explorateur de fichiers) pour décrire les fichiers ayant cette extension de fichier.  
  
 **Quel est le nom de la société à laquelle appartient le produit ?**  
 Nom de votre société.  
  
 Cette valeur est incorporée dans les propriétés AssemblyInfo de votre package DSL.  
  
 **Quel est l’espace de noms racine pour les projets dans cette solution ?**  
 L’emplacement par défaut pour un nom composé à partir de votre entreprise et les noms de produits.  
  
### <a name="signing-page"></a>Page signature  
 **Créer un fichier de clé de nom fort**  
 L’option par défaut est de créer une nouvelle clé pour signer votre assembly DSL.  
  
 **Utiliser une clé de nom fort existante**  
 Utilisez cette option si vous souhaitez intégrer votre DSL d’un autre assembly.  
  
 Pour plus d’informations sur les noms forts, consultez [création et assemblys avec nom fort](http://go.microsoft.com/fwlink/?LinkId=186073).  

## <a name="see-also"></a>Voir aussi

[Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)  
[Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
