---
title: Déploiement VSIX d’un DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916548"
---
# <a name="vsix-deployment-of-a-dsl"></a>Déploiement VSIX d’un DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez installer un langage spécifique à un domaine sur votre ordinateur ou sur d’autres ordinateurs. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doit déjà être installé sur l’ordinateur cible.

## <a name="Installing"></a>Installation et désinstallation d’une solution DSL à l’aide de la VSX
 Lorsque votre solution DSL est installée par cette méthode, l’utilisateur peut ouvrir un fichier DSL à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], mais ce fichier ne peut pas être ouvert à partir de l’Explorateur Windows.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>Pour installer une solution DSL à l’aide de l’extension VSIX

1. Sur votre ordinateur, recherchez le fichier **. vsix** généré par votre projet de package DSL.

    1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DslPackage** , puis cliquez sur **ouvrir le dossier dans l’Explorateur Windows**.

    2. Localisez le fichier **bin\\\*\\** _YourProject_ **. DslPackage. vsix**

2. Copiez le fichier **. vsix** sur l’ordinateur cible sur lequel vous souhaitez installer le DSL. Il peut s’agir de votre propre ordinateur ou d’un autre ordinateur.

    - L’ordinateur cible doit avoir l’une des éditions de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] qui prend en charge DSL au moment de l’exécution. Pour plus d’informations, consultez [éditions de Visual Studio prises en charge pour la visualisation & le kit de développement logiciel Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - L’ordinateur cible doit avoir l’une des éditions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spécifiées dans **DslPackage\source.extensions.manifest**.

3. Sur l’ordinateur cible, double-cliquez sur le fichier **. vsix** .

     Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.

4. Démarrez ou redémarrez [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. Pour tester le DSL, utilisez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer un nouveau fichier avec l’extension que vous avez définie pour votre DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Pour désinstaller un DSL qui a été installé à l’aide de VSX

1. Dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**.

2. Développez **Extensions installées**.

3. Sélectionnez l’extension dans laquelle la DSL est définie, puis cliquez sur **désinstaller**.

   Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier de l’emplacement suivant :

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**
