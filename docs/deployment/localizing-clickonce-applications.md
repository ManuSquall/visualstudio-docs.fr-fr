---
title: Localisation des Applications ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7897869e8cc010d54c1914cbfa8ca763dd3a3bfa
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279340"
---
# <a name="localize-clickonce-applications"></a>Localiser des applications ClickOnce
La localisation consiste à adapter votre application à une culture spécifique. Ce processus implique la traduction du texte de l'IU (interface utilisateur) dans une langue propre à la région, en utilisant la mise en forme appropriée de date et de devise, en ajustant la taille des contrôles sur un formulaire et en mettant en miroir les contrôles de droite à gauche, si nécessaire.  
  
 La localisation de votre application implique la création d'un ou plusieurs assemblys satellites. Chaque assembly contient des chaînes IU, des images et d'autres ressources spécifiques d'une culture donnée. (Le fichier exécutable principal de votre application contient les chaînes de la culture par défaut pour votre application.)  
  
 Cette rubrique décrit trois façons de déployer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour d'autres cultures :  
  
-   Inclure tous les assemblys satellites dans un déploiement unique.  
  
-   Générer un seul déploiement pour chaque culture, avec un seul assembly satellite chacune.  
  
-   Télécharger les assemblys satellites à la demande.  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Ajout de tous les assemblys satellites dans un déploiement  
 Au lieu de publier plusieurs déploiements [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous pouvez publier un seul déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui contient tous les assemblys satellites.  
  
 Cette méthode est utilisée par défaut dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour utiliser cette méthode dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous n'avez aucune autre tâche à effectuer.  
  
 Pour utiliser cette méthode avec *MageUI.exe*, vous devez définir la culture pour votre application à **neutre** dans *MageUI.exe*. Ensuite, vous devez inclure manuellement tous les assemblys satellites dans votre déploiement. Dans *MageUI.exe*, vous pouvez ajouter les assemblys satellites en utilisant le **Populate** bouton sur le **fichiers** onglet de votre manifeste d’application.  
  
 L'avantage de cette approche est de créer un déploiement unique et de simplifier votre histoire de déploiement localisé. Au moment de l'exécution, l'assembly satellite approprié est utilisé, en fonction de la culture par défaut du système d'exploitation Windows de l'utilisateur. L'inconvénient de cette approche est le téléchargement de tous les assemblys satellites chaque fois que l'application est installée ou mise à jour sur un ordinateur client. Si votre application comporte un grand nombre de chaînes ou que vos clients disposent d'une connexion réseau lente, ce processus peut affecter les performances pendant la mise à jour de l'application.  
  
> [!NOTE]
>  Cette approche suppose que votre application ajuste automatiquement la hauteur, la largeur et la position des contrôles pour s'adapter aux différentes tailles des chaînes de texte des différentes cultures. Windows Forms contient plusieurs contrôles et technologies qui vous permettent de concevoir votre formulaire de sorte à ce qu'il soit facilement localisable, y compris les contrôles <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel> ainsi que la propriété <xref:System.Windows.Forms.Control.AutoSize%2A>.  Consultez également [Comment : prendre en charge la localisation sur des formulaires Windows à l’aide du redimensionnement automatique et le contrôle TableLayoutPanel](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100)).  
  
## <a name="generate-one-deployment-for-each-culture"></a>Générer un déploiement pour chaque culture  
 Dans cette stratégie de déploiement, vous générez plusieurs déploiements. Dans chaque déploiement, vous incluez uniquement l'assembly satellite nécessaire pour une culture spécifique, et vous marquez le déploiement comme étant spécifique de cette culture.  
  
 Pour utiliser cette méthode dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], définissez le **Publish Language** propriété sur le **publier** onglet à la région souhaitée. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inclut automatiquement l'assembly satellite requis pour la région que vous sélectionnez et exclut tous les autres assemblys satellites du déploiement.  
  
 Vous pouvez accomplir la même chose en utilisant le *MageUI.exe* outil dans Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Utilisez le **Populate** bouton sur le **fichiers** onglet de votre manifeste d’application pour exclure tous les autres assemblys satellites à partir du répertoire de l’application, puis définissez le **Culture**champ sur le **nom** onglet manifeste de déploiement dans *MageUI.exe*. Ces étapes n'incluent pas seulement l'assembly satellite correct, elles définissent également l'attribut `language` de l'élément `assemblyIdentity` dans votre manifeste de déploiement avec la valeur de la culture correspondante.  
  
 Après la publication de l'application, vous devez répéter cette étape pour chaque culture supplémentaire que votre application prend en charge. Vous devez vous assurer que vous publiez vers un autre répertoire de serveur Web ou un répertoire de partage de fichier chaque fois, car chaque manifeste d’application référencera un assembly satellite différent et chaque manifeste de déploiement aura une valeur différente pour le `language`attribut.  
  
## <a name="download-satellite-assemblies-on-demand"></a>Télécharger des assemblys satellites à la demande  
 Si vous décidez d'inclure tous les assemblys satellites dans un déploiement unique, vous pouvez améliorer les performances à l'aide du téléchargement à la demande, qui vous permet de marquer des assemblys comme étant facultatifs. Les assemblys marqués ne sont pas téléchargés quand l'application est installée ou mise à jour. Vous pouvez installer les assemblys quand vous en avez besoin en appelant la méthode <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> sur la classe <xref:System.Deployment.Application.ApplicationDeployment>.  
  
 Le téléchargement d'assemblys satellites à la demande diffère légèrement du téléchargement d'autres types d'assemblys à la demande. Pour plus d’exemples de code et des informations sur la façon d’activer ce scénario à l’aide de la [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] tools pour [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consultez [procédure pas à pas : téléchargement d’assemblys satellites à la demande avec l’API de déploiement ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).  
  
 Vous pouvez également mettre en place ce scénario dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Consultez également [procédure pas à pas : téléchargement d’assemblys satellites à la demande avec le ClickOnce déploiement API en utilisant le concepteur](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) ou [procédure pas à pas : téléchargement d’assemblys satellites à la demande avec l’API de déploiement ClickOnce L’aide du concepteur](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>Test des applications ClickOnce localisées avant le déploiement  
 Un assembly satellite est utilisé pour une application Windows Forms uniquement si la propriété <xref:System.Threading.Thread.CurrentUICulture%2A> pour le thread principal de l'application est définie avec la valeur de la culture de l'assembly satellite. Les clients des marchés locaux ont probablement déjà exécuté une version localisée de Windows avec une culture définie avec la valeur par défaut appropriée.  
  
 Vous avez trois options pour tester les déploiements localisés avant de mettre votre application à la disposition des clients :  
  
-   Vous pouvez exécuter votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sur les versions localisées de Windows appropriées.  
  
-   Vous pouvez définir la propriété <xref:System.Threading.Thread.CurrentUICulture%2A> par programmation dans votre application. (Cette propriété doit être définie avant d'appeler la méthode <xref:System.Windows.Forms.Application.Run%2A>.)  
  
## <a name="see-also"></a>Voir aussi  
 [\<assemblyIdentity > élément](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Globaliser les formulaires Windows](/dotnet/framework/winforms/advanced/globalizing-windows-forms)