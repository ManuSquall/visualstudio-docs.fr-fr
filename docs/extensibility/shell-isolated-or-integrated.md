---
title: "Shell (isolé ou intégré) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ed0e82dbc2c093a94080fe3fcf07a3e3b20e1a50
ms.lasthandoff: 02/22/2017

---
# <a name="shell-isolated-or-integrated"></a>Shell (isolé ou intégré)
Vous pouvez créer votre propre application Visual Studio en mode intégré ou isolé. En mode intégré, les nombreuses fonctionnalités de Visual Studio sont disponibles en plus de votre application. En mode isolé, vous choisissez un sous-ensemble des fonctionnalités de Visual Studio que vous souhaitez distribuer avec votre propre extension.  
  
## <a name="integrated-mode"></a>En Mode intégré  
 Mode intégré permet à vos utilisateurs d’utiliser les fonctionnalités de Visual Studio standard, ainsi que des outils personnalisés. L’environnement intégré est conçu principalement pour l’hébergement de langages de programmation et les outils de développement logiciel.  
  
 Les outils personnalisés qui sont créées automatiquement sur l’environnement intégré de fusion avec une autre édition de Visual Studio est installé sur le même ordinateur. Vous pouvez fournir une version redistribuable du shell Visual Studio intégré si Visual Studio n’est pas déjà installé.  
  
 La version redistribuable de l’environnement intégré de Visual Studio n’inclut pas de langages de programmation et les fonctionnalités qui prennent en charge leurs systèmes de projet respectifs.  
  
> [!NOTE]
>  Le mode intégré de Visual Studio shell peut être installé avec toutes les éditions de Visual Studio, sauf les éditions Express.  
  
 Pour plus d’informations, consultez [Visual Studio Shell (intégré)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>En Mode isolé  
 Mode isolé vous permet de créer des outils personnalisés qui s’exécutent côte à côte avec d’autres versions de Visual Studio. Elle est principalement destinée aux outils qui peuvent accéder aux services de Visual Studio sans en fonction de toutes les fonctionnalités de Visual Studio standards. Vous pouvez personnaliser l’apparence des applications basées sur le shell Visual Studio isolé. Vous pouvez facilement désactiver les fonctionnalités et les groupes de commandes de menu que vous ne souhaitez pas apparaître avec votre application.  
  
 Pour plus d’informations, consultez [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribution de votre Application Shell intégré ou isolé  
 Pour distribuer votre application shell intégré ou isolés, vous devez inclure votre application, un environnement d’intégré ou isolée spécial redistribuable et un programme d’installation. Pour plus d’informations sur l’installation et la distribution, consultez [distribution des Applications de Shell isolé](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Le [contrat de licence utilisateur final (CLUF)](https://www.visualstudio.com/en-us/support/legal/mt171552) pour Visual Studio intégré et isolé shells comprend une section sur la collecte de données (**Section 3. Data**).  Il décrit les données d’utilisation de client qui peuvent être collectées par Microsoft aux utilisateurs que les logiciels de shell intégré ou isolé que vous générez dans votre application. Pour plus d’informations, consultez [déclaration de confidentialité Microsoft Visual Studio produit famille](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Si vous collectez des données d’utilisation de distinct de vos clients à travers votre application, vous devez fournir des avis appropriés aux utilisateurs de votre application de ce que vous collectez.  Lorsque vous distribuez le logiciel shell isolé ou intégré dans le cadre de votre application, en fonction de la licence Visual Studio Software Development Kit, vous devez inclure une des opérations suivantes :  
>   
>  -   le contrat de licence utilisateur final dans le cadre de votre licence de l’application  
> -   votre propre CLUF qui nécessite de vos clients accepter les termes qui protègent le Visual Studio intégré ou isolés shell au moins autant que le contrat de licence utilisateur final Microsoft pour le logiciel de l’interpréteur de commandes  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d’informations sur les packages redistribuables, consultez le [téléchargements Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) site Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
