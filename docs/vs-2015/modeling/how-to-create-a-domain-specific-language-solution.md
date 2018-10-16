---
title: 'Comment : créer une Solution de langage spécifique à un domaine | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: cf28035726f20aa715bfe12a48b1378edfacb673
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223213"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Comment : créer une solution de langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un langage spécifique à un domaine (DSL) est créé à l’aide de spécialisé [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solution.  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de commencer cette procédure, vous devez d’abord installer ces composants :  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-a-domain-specific-language-solution"></a>Création d’une Solution de langage spécifique à un domaine  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Pour créer une solution de langage spécifique à un domaine  
  
1.  Démarrez l’Assistant DSL.  
  
    1.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
    2.  La boîte de dialogue **Nouveau projet** s’affiche.  
  
    3.  Sous **types de projets**, développez le **autres Types de projets** nœud, puis cliquez sur **extensibilité**.  
  
    4.  Cliquez sur **Domain-Specific Language concepteur**.  
  
    5.  Dans le **nom** , tapez un nom pour la solution. Cliquez sur **OK**.  
  
         Le **Assistant Concepteur de langage spécifique à un domaine** s’affiche.  
  
        > [!NOTE]
        >  De préférence, le nom que vous tapez doit être un identificateur c# valide, car elle peut être utilisée pour générer le code.  
  
     ![Boîte de dialogue DSL créer](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2.  Choisissez un modèle DSL.  
  
     Sur le **sélectionner les Options de langage spécifique à un domaine** page, sélectionnez un des modèles de solution tel que **langage Minimal**. Choisissez un modèle qui est similaire à la solution DSL que vous souhaitez créer.  
  
     Pour plus d’informations sur les modèles de solution, consultez [choix d’un modèle de Solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3.  Entrez une extension de nom de fichier le **Extension de fichier** page. Il doit être unique dans votre ordinateur, et dans tous les ordinateurs sur lesquels vous souhaitez installer la solution DSL. Vous devez voir le message **aucune application ou les éditeurs de Visual Studio n’utilisent cette extension**.  
  
    -   Si vous avez utilisé l’extension de nom de fichier dans la précédente DSL expérimentale qui n’ont pas été entièrement installé, vous pouvez les désactiver arrière à l’aide de la **réinitialiser l’Instance expérimentale** outil, qui se trouve dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menu du Kit de développement logiciel.  
  
    -   Si un autre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension qui utilise cette extension de fichier a été entièrement installée sur votre ordinateur, envisagez de le désinstaller. Sur le **outils** menu, cliquez sur **Gestionnaire d’extensions**.  
  
4.  Examiner et ajuster si nécessaire, les champs dans les pages restantes de l’Assistant. Lorsque vous êtes satisfait des paramètres, cliquez sur **Terminer**. Pour plus d’informations sur les paramètres, consultez [Pages de l’Assistant concepteur DSL](#settings).  
  
     L’Assistant crée une solution qui comporte deux projets, qui sont nommés **Dsl** et **DslPackage**.  
  
    > [!NOTE]
    >  Si vous voyez un message qui vous n'avertit pas pour exécuter des modèles de texte à partir de sources non fiables, cliquez sur **OK**. Vous pouvez définir ce message ne pas s’affiche à nouveau.  
  
##  <a name="settings"></a> Les Pages d’Assistant concepteur DSL  
 Vous pouvez laisser certains des champs inchangés à partir de leurs valeurs par défaut. Toutefois, assurez-vous que vous définissez le champ d’Extension de fichier.  
  
### <a name="solution-settings-page"></a>Page Paramètres de la solution  
 **Le modèle que vous souhaitez baser votre langage spécifique à un domaine sur ?**  
 Choisissez un modèle qui est similaire à la solution DSL que vous souhaitez créer. Les différents modèles fournissent des points de départ pratiques. Lorsque vous sélectionnez un modèle de solution, l’Assistant affiche une description. Pour plus d’informations sur les modèles de solution, consultez [choix d’un modèle de Solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **Que voulez-vous nommer votre langage spécifique à un domaine ?**  
 La valeur par défaut est le nom de la solution. Code est généré à partir de cette valeur. Il doit être valide comme nom de classe c#.  
  
### <a name="file-extension-page"></a>Page Extension de fichier  
 **Quelle extension doit modéliser fichiers utilisent ?**  
 Tapez une nouvelle extension de fichier.  
  
 Vérifiez que cette extension de fichier n'a pas déjà été inscrit pour une utilisation dans cet ordinateur, comme suit :  
  
 Regardez sous **autres outils et applications inscrit pour gérer cette extension**. Si vous voyez le message **aucune application ou les éditeurs de Visual Studio n’utilisent cette extension**, vous pouvez ensuite utiliser cette extension de fichier.  
  
 Si vous voyez une liste d’outils ou des packages, vous devez effectuer une des opérations suivantes :  
  
-   Tapez une extension de fichier différent.  
  
     \- ou -  
  
-   Réinitialiser le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Instance expérimentale. Annule toutes des DSL que vous avez créées précédemment. Sur le **Démarrer** menu, cliquez sur **tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **outils**, puis **réinitialiser le Instance de Microsoft Visual Studio 2010 expérimentale**. Vous pouvez reconstruire les autres DSL que vous souhaitez utiliser à nouveau.  
  
     \- ou -  
  
-   Si un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension qui utilise cette extension de fichier a été entièrement installée sur votre ordinateur, désinstallez-le. Sur le **outils** menu, cliquez sur **Gestionnaire d’extensions**.  
  
### <a name="product-settings-page"></a>Page des paramètres de produit  
 **Quel est le nom du produit auquel appartient le nouveau langage spécifique à un domaine ?**  
 La valeur par défaut est le nom DSL.  
  
 Cette valeur est utilisée dans l’Explorateur Windows (ou Explorateur de fichiers) pour décrire les fichiers ayant cette extension de fichier.  
  
 **Quel est le nom de la société à laquelle appartient le produit ?**  
 Nom de votre société.  
  
 Cette valeur est incorporée dans les propriétés AssemblyInfo de votre package DSL.  
  
 **Quel est l’espace de noms racine pour les projets dans cette solution ?**  
 Par défaut est un nom composé à partir de votre entreprise et les noms de produits.  
  
### <a name="signing-page"></a>Page de signature  
 **Créer un fichier de clé de nom fort**  
 L’option par défaut consiste à créer une nouvelle clé pour signer votre assembly DSL.  
  
 **Utiliser une clé de nom fort existante**  
 Utilisez cette option si vous souhaitez intégrer votre solution DSL avec un autre assembly.  
  
 Pour plus d’informations sur l’utilisation de noms forts, consultez [création et assemblys avec nom fort](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)   
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



