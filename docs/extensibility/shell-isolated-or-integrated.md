---
redirect_url: shell/shell-isolated-or-integrated
title: "Shell (isolé ou intégré) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f06af0b884d404b3fd2e8e36cac235c10d254bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell (isolé ou intégré)
Vous pouvez créer votre propre application Visual Studio en mode intégré ou isolé. En mode intégré, de nombreuses fonctionnalités de Visual Studio sont disponibles en plus de votre application. En mode isolé, vous choisissez un sous-ensemble des fonctionnalités de Visual Studio que vous souhaitez distribuer avec votre propre extension.  
  
## <a name="integrated-mode"></a>En Mode intégré  
 En mode intégré permet à vos utilisateurs à utiliser les fonctionnalités de Visual Studio standard, ainsi que des outils personnalisés. L’environnement intégré est principalement destinée aux langages de programmation et les outils de développement logiciel d’hébergement.  
  
 Des outils personnalisés qui sont créées automatiquement sur l’environnement intégré de fusion avec une autre édition de Visual Studio est installé sur le même ordinateur. Vous pouvez fournir une version redistribuable de l’interpréteur de commandes de Visual Studio intégré si Visual Studio n’est pas déjà installé.  
  
 La version redistribuable de l’interpréteur de commandes intégré de Visual Studio n’inclut pas de langages de programmation et les fonctionnalités qui prennent en charge leurs systèmes de projet respectifs.  
  
> [!NOTE]
>  Le mode intégré de Visual Studio shell peut être installé avec toutes les éditions de Visual Studio, à l’exception des éditions Express.  
  
 Pour plus d’informations, consultez [Visual Studio Shell (intégré)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Mode isolé  
 Mode isolé vous permet de créer des outils personnalisés qui s’exécutent côte à côte avec d’autres versions de Visual Studio. Il est principalement destinée aux outils qui peuvent accéder aux services de Visual Studio sans en fonction de toutes les fonctionnalités Visual Studio standards. Vous pouvez personnaliser l’apparence des applications basées sur le shell isolé Visual Studio. Vous pouvez facilement désactiver les fonctionnalités et les groupes de commandes de menu que vous ne souhaitez pas apparaître avec votre application.  
  
 Pour plus d’informations, consultez [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribution de votre Application de Shell intégré ou isolé  
 Afin de pouvoir distribuer votre application de shell intégré ou isolés, vous devez inclure votre application, un intégré ou isolé interpréteur de commandes spécial redistribuable et un programme d’installation. Pour plus d’informations sur la distribution et d’installation, consultez [distribution des Applications de Shell isolé](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Le [contrat de licence utilisateur final (CLUF)](https://www.visualstudio.com/en-us/support/legal/mt171552) pour Visual Studio intégré et isolé interpréteurs de commandes inclut une section sur la collecte de données (**Section 3. Données**).  Elle décrit les données d’utilisation client qui peuvent être collectées par Microsoft, des utilisateurs du logiciel shell intégré ou isolé que vous générez dans votre application. Pour plus d’informations, consultez [déclaration de confidentialité Microsoft Visual Studio produit famille](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Si vous collectez des données d’utilisation de distinct à partir de vos clients à travers votre application, vous devez fournir les avis appropriés aux utilisateurs de votre application de ce que vous collectez.  Lorsque vous distribuez le logiciel shell isolé ou intégré dans le cadre de votre application, en fonction de la licence du Kit de développement Visual Studio logiciel, vous devez inclure un des éléments suivants :  
>   
>  -   le contrat de licence utilisateur final dans le cadre de votre licence de l’application  
> -   votre propre CLUF qui nécessite de vos clients à accepter les termes qui protègent le Visual Studio intégré ou isolés shell au moins autant que les termes du contrat de licence utilisateur final Microsoft pour le logiciel de l’interpréteur de commandes  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d’informations sur les packages redistribuables, consultez le [téléchargements d’extensibilité Visual Studio](http://go.microsoft.com/fwlink/?LinkID=119298) site Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)