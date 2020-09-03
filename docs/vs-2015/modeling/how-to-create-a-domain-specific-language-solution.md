---
title: 'Comment : créer une solution de langage spécifique à un domaine | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 227838334067d33c8a50c81d3a3c013c6baee356
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533079"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Comment : créer une solution de langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un langage spécifique à un domaine (DSL) est créé à l’aide d’une [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solution spécialisée.

## <a name="prerequisites"></a>Prérequis
 Avant de commencer cette procédure, vous devez d’abord installer les composants suivants :

|Produit|Télécharger le lien|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[SDK Visual Studio](../extensibility/visual-studio-sdk.md)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[Téléchargement du SDK Modeling](https://www.microsoft.com/download/details.aspx?id=48148)|

## <a name="creating-a-domain-specific-language-solution"></a>Création d’une solution de langage spécifique à un domaine

#### <a name="to-create-a-domain-specific-language-solution"></a>Pour créer une solution de langage spécifique à un domaine

1. Démarrez l’Assistant DSL.

   1. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

   2. La boîte de dialogue **Nouveau projet** apparaît.

   3. Sous **types de projets**, développez le nœud **autres types de projets** , puis cliquez sur **extensibilité**.

   4. Cliquez sur **Concepteur Domain-specific language**.

   5. Dans la zone **nom** , tapez un nom pour la solution. Cliquez sur **OK**.

       L' **assistant concepteur Domain-specific language** s’affiche.

      > [!NOTE]
      > De préférence, le nom que vous tapez doit être un identificateur Visual C# valide, car il peut être utilisé pour générer du code.

      ![Boîte de dialogue Créer DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")

2. Choisissez un modèle DSL.

    Dans la page **Sélectionner les options de langage spécifique à un domaine** , sélectionnez l’un des modèles de solution, par exemple **langue minimale**. Choisissez un modèle similaire à la DSL que vous souhaitez créer.

    Pour plus d’informations sur les modèles de solution, consultez [choix d’un modèle de solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Entrez une extension de nom de **fichier** dans la page extension de fichier. Elle doit être unique sur votre ordinateur et sur tous les ordinateurs sur lesquels vous souhaitez installer le DSL. Vous devez voir le message **aucune application ou éditeur Visual Studio n’utilise cette extension**.

   - Si vous avez utilisé l’extension de nom de fichier dans les DSL expérimentaux précédents qui n’ont pas été entièrement installés, vous pouvez les supprimer à l’aide de l’outil **réinitialisation de l’instance expérimentale** , qui se trouve dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] menu du kit de développement logiciel (SDK).

   - Si une autre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extension qui utilise cette extension de fichier a été entièrement installée sur votre ordinateur, envisagez de la désinstaller. Dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**.

4. Inspectez et, si nécessaire, ajustez les champs dans les pages restantes de l’Assistant. Lorsque vous êtes satisfait des paramètres, cliquez sur **Terminer**. Pour plus d’informations sur les paramètres, consultez [Concepteur DSL pages](#settings)de l’Assistant.

    L’Assistant crée une solution qui a deux projets, nommés **DSL** et **DslPackage**.

   > [!NOTE]
   > Si un message s’affiche pour vous avertir que vous n’exécutez pas de modèles de texte provenant de sources non approuvées, cliquez sur **OK**. Vous pouvez définir ce message pour qu’il ne s’affiche plus.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a> Pages de l’Assistant Concepteur DSL
 Vous pouvez ne pas modifier les valeurs par défaut de plusieurs champs. Toutefois, veillez à définir le champ extension de fichier.

### <a name="solution-settings-page"></a>Page Paramètres de la solution
 **Sur quel modèle souhaitez-vous baser votre langage spécifique à un domaine ?**
Choisissez un modèle similaire à la DSL que vous souhaitez créer. Les différents modèles offrent des points de départ pratiques. Lorsque vous sélectionnez un modèle de solution, l’Assistant affiche une description. Pour plus d’informations sur les modèles de solution, consultez [choix d’un modèle de solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Comment voulez-vous nommer votre langage spécifique à un domaine ?**
La valeur par défaut est le nom de la solution. Le code est généré à partir de cette valeur. Elle doit être valide en tant que nom de classe C#.

### <a name="file-extension-page"></a>Page extension de fichier
 **Quelle extension les fichiers doivent-ils utiliser ?**
Tapez une nouvelle extension de fichier.

 Vérifiez que cette extension de fichier n’a pas déjà été inscrite pour être utilisée sur cet ordinateur, comme suit :

 Recherchez dans **d’autres outils et applications enregistrés pour gérer cette extension**. Si vous voyez le message **aucune application ou aucun éditeur Visual Studio n’utilise cette extension**, vous pouvez utiliser cette extension de fichier.

 Si vous voyez une liste d’outils ou de packages, vous devez effectuer l’une des opérations suivantes :

- Tapez une extension de fichier différente.

     \- ou -

- Réinitialisez l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instance expérimentale. Cela annule l’enregistrement de tous les DSL que vous avez générés précédemment. Dans le menu **Démarrer** , cliquez **sur tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **Outils**, puis **réinitialisez l’instance Microsoft Visual Studio 2010 expérimentale**. Vous pouvez régénérer tout autre DSL que vous souhaitez réutiliser.

     \- ou -

- Si une [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extension qui utilise cette extension de fichier a été entièrement installée sur votre ordinateur, désinstallez-la. Dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**.

### <a name="product-settings-page"></a>Page Paramètres du produit
 **Quel est le nom du produit auquel appartient le nouveau langage spécifique à un domaine ?**
La valeur par défaut est le nom DSL.

 Cette valeur est utilisée dans l’Explorateur Windows (ou l’Explorateur de fichiers) pour décrire les fichiers qui ont cette extension de fichier.

 **Quel est le nom de la société à laquelle le produit appartient ?**
Nom de votre société.

 Cette valeur est incorporée dans les propriétés AssemblyInfo de votre package DSL.

 **Qu’est-ce que l’espace de noms racine des projets dans cette solution ?**
Par défaut, il s’agit d’un nom composé des noms de votre entreprise et de votre produit.

### <a name="signing-page"></a>Page signature
 **Créer un fichier de clé de nom fort** L’option par défaut consiste à créer une nouvelle clé pour signer votre assembly DSL.

 **Utiliser une clé de nom fort existante** Utilisez cette option si vous souhaitez intégrer votre DSL à un autre assembly.

 Pour plus d’informations sur l’affectation d’un nom fort, consultez [création et utilisation d’assemblys avec nom fort](/dotnet/standard/assembly/create-use-strong-named).

## <a name="see-also"></a>Voir aussi
 [Comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md) [Outils Domain-specific language Glossaire](/previous-versions/bb126564(v=vs.100))
