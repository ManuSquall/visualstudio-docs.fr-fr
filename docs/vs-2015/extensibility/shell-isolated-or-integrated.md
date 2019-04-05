---
title: Shell (isolé ou intégré) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d8b08dfe812245a21160fa2f16b4c94728785ae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952617"
---
# <a name="shell-isolated-or-integrated"></a>Shell (isolé ou intégré)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer votre propre application basée sur Visual Studio en mode intégré ou isolé. En mode intégré, les nombreuses fonctionnalités de Visual Studio sont disponibles en plus de votre application. En mode isolé, vous choisissez un sous-ensemble de fonctionnalités de Visual Studio que vous souhaitez distribuer avec votre propre extension.  
  
## <a name="integrated-mode"></a>En Mode intégré  
 Mode intégré permet à vos utilisateurs à utiliser les fonctionnalités de Visual Studio standard, ainsi que vos outils personnalisés. Le shell intégré est destiné principalement à l’hébergement des langages de programmation et les outils de développement logiciel.  
  
 Les outils personnalisés qui sont créées automatiquement sur le shell intégré fusionnent avec toute autre édition de Visual Studio est installé sur le même ordinateur. Vous pouvez fournir une version redistribuable de l’interpréteur de commandes de Visual Studio intégré si Visual Studio n’est pas déjà installé.  
  
 La version redistribuable du shell intégré de Visual Studio n’inclut pas de langages de programmation et les fonctionnalités qui prennent en charge de leurs systèmes de projet respectifs.  
  
> [!NOTE]
>  Le mode intégré de Visual Studio shell peut être installé avec toutes les éditions de Visual Studio, sauf les éditions Express.  
  
 Pour plus d’informations, consultez [Visual Studio Shell (intégré)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Mode isolé  
 Mode isolé, vous pouvez créer des outils personnalisés qui s’exécutent côte à côte avec d’autres versions de Visual Studio. Il est principalement destinée aux outils qui peuvent accéder aux services Visual Studio sans en fonction de toutes les fonctionnalités de Visual Studio standards. Vous pouvez personnaliser l’apparence des applications générées sur le shell isolé Visual Studio. Vous pouvez facilement désactiver les fonctionnalités et les groupes de commandes de menu que vous ne souhaitez pas apparaître avec votre application.  
  
 Pour plus d’informations, consultez [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribution de votre Application de Shell intégré ou isolé  
 Pour distribuer votre application de shell intégré ou isolé, vous devez inclure votre application, un shell d’intégré ou isolé spécial redistribuable et un programme d’installation. Pour plus d’informations sur la distribution et l’installation, consultez [distribution d’Applications Shell isolé](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Le [contrat de licence utilisateur final (CLUF)](https://www.visualstudio.com/support/legal/mt171552) pour Visual Studio intégré et isolé interpréteurs de commandes inclut une section sur la collecte de données (**Section 3. Données**).  Il décrit les données d’utilisation client qui peuvent être collectées par Microsoft avec les utilisateurs du logiciel shell intégré ou isolé que vous intégrez votre application. Pour plus d’informations, consultez [Visual Studio produit déclaration de confidentialité Microsoft](https://www.visualstudio.com/dn948229).  
> 
>  Si vous collectez des données d’utilisation distincts à partir de vos clients via votre application, vous devez fournir des avis approprié aux utilisateurs de votre application de ce que vous collectez.  Lorsque vous distribuez le logiciel shell isolé ou intégré dans le cadre de votre application, en fonction de la licence Visual Studio Software Development Kit, vous devez inclure un des éléments suivants :  
> 
> - le contrat de licence utilisateur final dans le cadre de votre licence de l’application  
>   -   votre propre CLUF qui nécessite de vos clients à accepter les termes qui protègent le Visual Studio intégré ou isolé de shell au moins autant que les termes de licence utilisateur final Microsoft pour le logiciel de l’interpréteur de commandes  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d’informations sur les packages redistribuables, consultez le [téléchargements de Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) site Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
