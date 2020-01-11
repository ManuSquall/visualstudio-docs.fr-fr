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
ms.openlocfilehash: aa346ebfe321e4672ea3fa71a4dcc872ebf22cda
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850232"
---
# <a name="shell-isolated-or-integrated"></a>Shell (isolé ou intégré)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer votre propre application basée sur Visual Studio en mode intégré ou isolé. En mode intégré, de nombreuses fonctionnalités de Visual Studio sont disponibles en plus de votre application. En mode isolé, vous choisissez un sous-ensemble de fonctionnalités de Visual Studio que vous souhaitez distribuer avec votre propre extension.  
  
## <a name="integrated-mode"></a>Mode intégré  
 Le mode intégré permet à vos utilisateurs d’utiliser les fonctionnalités Visual Studio standard, ainsi que vos outils personnalisés. L’interpréteur de commandes intégré est principalement destiné à l’hébergement des langages de programmation et des outils de développement de logiciels.  
  
 Les outils personnalisés basés sur l’interpréteur de commandes intégré sont automatiquement fusionnés avec toute autre édition de Visual Studio installée sur le même ordinateur. Vous pouvez fournir une version redistribuable de l’interpréteur de commandes intégré de Visual Studio si Visual Studio n’est pas déjà installé.  
  
 La version redistribuable de l’interpréteur de commandes intégré de Visual Studio n’inclut pas les langages de programmation et les fonctionnalités qui prennent en charge leurs systèmes de projet respectifs.  
  
> [!NOTE]
> Le mode intégré de Visual Studio Shell peut être installé avec toutes les éditions de Visual Studio, à l’exception des éditions Express.  
  
 Pour plus d’informations, consultez [Visual Studio Shell (intégré)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Mode isolé  
 Le mode isolé vous permet de créer des outils personnalisés qui s’exécutent côte à côte avec d’autres versions de Visual Studio. Il est principalement destiné aux outils qui peuvent accéder aux services Visual Studio sans dépendre de toutes les fonctionnalités standard de Visual Studio. Vous pouvez personnaliser l’apparence des applications basées sur le shell isolé Visual Studio. Vous pouvez facilement désactiver les fonctionnalités et les groupes de commandes de menu que vous ne souhaitez pas voir apparaître avec votre application.  
  
 Pour plus d’informations, consultez [Visual Studio isolated Shell](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribution de votre application d’interpréteur de commandes intégrée ou isolée  
 Pour distribuer votre application d’interpréteur de commandes intégrée ou isolée, vous devez inclure votre application, un package redistribuable d’interpréteur de commandes intégré ou isolé, ainsi qu’un programme d’installation. Pour plus d’informations sur la distribution et l’installation, consultez [distribution d’applications Shell isolées](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
> Le [contrat de licence utilisateur final (CLUF)](https://www.visualstudio.com/support/legal/mt171552) des shells intégrés et isolés de Visual Studio comprend une section sur la collecte de données (**section 3). Données**).  Il décrit les données d’utilisation client qui peuvent être collectées par Microsoft auprès des utilisateurs du logiciel de Shell intégré ou isolé que vous intégrez dans votre application. Pour plus d’informations, consultez [Microsoft Visual Studio déclaration de confidentialité](https://www.visualstudio.com/dn948229)de la famille de produits.  
> 
> Si vous collectez des données d’utilisation distinctes de vos clients par le biais de votre application, vous devez fournir une notification appropriée aux utilisateurs de votre application que vous recueillez.  Lorsque vous distribuez le logiciel de Shell isolé ou intégré dans le cadre de votre application, conformément à la licence du kit de développement logiciel (SDK) Visual Studio, vous devez inclure l’un des éléments suivants :  
> 
> - Contrat de licence utilisateur final dans le cadre de votre licence d’application  
> - votre propre CLUF qui oblige vos clients à accepter les termes qui protègent le shell intégré ou isolé de Visual Studio au moins aussi bien que les termes du contrat de licence utilisateur final Microsoft pour le logiciel de Shell  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d’informations sur les packages redistribuables, consultez le site Web des téléchargements de l' [extensibilité Visual Studio](https://msdn.microsoft.com/vstudio/bb984878.aspx) .  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
