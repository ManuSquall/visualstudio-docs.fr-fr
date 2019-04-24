---
title: 'Procédure : Créer une solution de langage spécifique à un domaine'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b1799ac2e7124f79d10dcc8860a994e2f182ea7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051347"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Procédure : Créer une solution de langage spécifique à un domaine
Un langage spécifique à un domaine (DSL) est créé à l’aide d’une solution Visual Studio spécialisée.

## <a name="prerequisites"></a>Prérequis

Avant de commencer cette procédure, installez ces composants :

- Visual Studio
- Kit de développement logiciel Visual Studio (installé dans le cadre de la **développement d’extensions Visual Studio** charge de travail)
- Modélisation du Kit de développement logiciel (installé comme un composant de Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Création d’une Solution de langage spécifique à un domaine

1. Démarrer l’Assistant de DSL en créant un nouveau **Concepteur de langage spécifique à un domaine** projet.

   > [!NOTE]
   > De préférence, le nom que vous choisissez pour le projet doit être un élément visuel valid C# identificateur, car elle peut être utilisée pour générer le code.

   ::: moniker range="vs-2017"

   ![Boîte de dialogue Créer DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Choisissez un modèle DSL.

    Sur le **sélectionner les Options de langage spécifique à un domaine** page, sélectionnez un des modèles de solution tel que **langage Minimal**. Choisissez un modèle qui est similaire à la solution DSL que vous souhaitez créer.

    Pour plus d’informations sur les modèles de solution, consultez [choix d’un modèle de Solution de langage spécifique à un domaine](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Entrez une extension de nom de fichier le **Extension de fichier** page. Il doit être unique dans votre ordinateur, et dans tous les ordinateurs sur lesquels vous souhaitez installer la solution DSL. Vous devez voir le message **aucune application ou les éditeurs de Visual Studio n’utilisent cette extension**.

   - Si vous avez utilisé l’extension de nom de fichier dans la précédente DSL expérimentale qui n’ont pas été entièrement installé, vous pouvez les désactiver arrière à l’aide de la **réinitialiser l’Instance expérimentale** outil, qui se trouve dans le menu Visual Studio SDK.

   - Si une autre Extension Visual Studio qui utilise cette extension de fichier a été entièrement installée sur votre ordinateur, envisagez de le désinstaller. Sur le **outils** menu, cliquez sur **Gestionnaire d’extensions**.

4. Examiner et ajuster si nécessaire, les champs dans les pages restantes de l’Assistant. Lorsque vous êtes satisfait des paramètres, cliquez sur **Terminer**. Pour plus d’informations sur les paramètres, consultez [Pages de l’Assistant concepteur DSL](#settings).

    L’Assistant crée une solution qui comporte deux projets, qui sont nommés **Dsl** et **DslPackage**.

   > [!NOTE]
   >  Si vous voyez un message qui vous n'avertit pas pour exécuter des modèles de texte à partir de sources non fiables, cliquez sur **OK**. Vous pouvez définir ce message ne pas s’affiche à nouveau.

## <a name="settings"></a> Les Pages d’Assistant concepteur DSL
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

- Tapez une extension de fichier différent.

     \- ou -

- Réinitialiser l’Instance expérimentale de Visual Studio. Annule toutes des DSL que vous avez créées précédemment. Sur le **Démarrer** menu, cliquez sur **tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **outils**, puis **réinitialiser le Instance de Microsoft Visual Studio 2010 expérimentale**. Vous pouvez reconstruire les autres DSL que vous souhaitez utiliser à nouveau.

     \- ou -

- Si une Extension Visual Studio qui utilise cette extension de fichier a été entièrement installée sur votre ordinateur, désinstallez-la. Sur le **outils** menu, cliquez sur **Gestionnaire d’extensions**.

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
 **Créer un fichier de clé de nom fort** l’option par défaut consiste à créer une nouvelle clé pour signer votre assembly DSL.

 **Utiliser la clé de nom fort existant** Utilisez cette option si vous souhaitez intégrer votre solution DSL avec un autre assembly.

 Pour plus d’informations sur l’utilisation de noms forts, consultez [création et assemblys avec nom fort](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)
- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
