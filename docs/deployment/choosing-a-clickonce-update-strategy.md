---
title: Choix d’une stratégie de mise à jour ClickOnce | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08025ed5d5e3806e04501c46a96e1df5f85b31fb
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="choosing-a-clickonce-update-strategy"></a>Choix d'une stratégie de mise à jour ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut fournir des mises à jour d'application automatiques. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application lit périodiquement son fichier manifeste de déploiement pour voir si des mises à jour de l’application sont disponibles. Si disponible, la nouvelle version de l'application est téléchargée et exécutée. Pour des raisons d'efficacité, seuls les fichiers modifiés sont téléchargés.  
  
 Lorsque vous concevez une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous devez déterminer quelle stratégie l'application utilisera pour vérifier les mises à jour disponibles. Trois stratégies de base sont possibles : la vérification des mises à jour au démarrage de l'application, la vérification des mises à jour après le démarrage de l'application (exécutée dans un thread d'arrière-plan) ou la présentation d'une interface utilisateur destinée aux mises à jour.  
  
 De plus, vous pouvez déterminer la fréquence de vérification des mises à jour effectuées par l'application et configurer une mise à jour obligatoire.  
  
> [!NOTE]
>  Les mises à jour d'application exigent une connexion au réseau. En l'absence d'une connexion réseau, l'application s'exécute sans vérifier les mises à jour, quelle que soit la stratégie de mise à jour choisie.  
  
> [!NOTE]
>  Dans le .NET Framework 2.0 et le .NET Framework 3.0, à chaque fois que votre application vérifie les mises à jour, avant ou après le démarrage, ou à l'aide des API <xref:System.Deployment.Application>, vous devez définir `deploymentProvider` dans le manifeste de déploiement. Le `deploymentProvider` élément correspondant dans Visual Studio pour le **mettre à jour d’emplacement** champ sur la **mises à jour** boîte de dialogue de la **publier** onglet. Cette règle est assouplie dans .NET Framework 3.5. Pour plus d’informations, consultez [déploiement ClickOnce Applications pour tester les et les serveurs de Production sans Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).  
  
## <a name="checking-for-updates-after-application-startup"></a>Vérification des mises à jour après le démarrage de l'application  
 Si vous utilisez cette stratégie, l'application tente de localiser et de lire le fichier manifeste de déploiement en arrière-plan pendant l'exécution de l'application. Si une mise à jour est disponible, lors de la prochaine exécution de l'application, l'utilisateur sera invité à télécharger et à installer la mise à jour.  
  
 Cette stratégie est tout particulièrement adaptée aux connexions réseau à bande passante restreinte ou aux applications plus importantes, susceptibles de nécessiter de longs téléchargements.  
  
 Pour activer cette stratégie de mise à jour, cliquez sur **après le démarrage de l’application** dans les **choisissez à quel moment l’application doit vérifier les mises à jour** section de la **mises à jour de l’Application** boîte de dialogue. Puis spécifiez un intervalle de mise à jour dans la section **spécifier la fréquence à laquelle l’application doit vérifier les mises à jour**.  
  
 Cela revient à modifier le **mise à jour** manifeste d’élément dans le déploiement comme suit :  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>Vérification des mises à jour avant le démarrage de l'application  
 La stratégie par défaut est d'essayer de localiser et de lire le fichier manifeste de déploiement avant le démarrage de l'application. Avec cette stratégie, l'application tente de localiser et de lire le fichier manifeste de déploiement chaque fois que l'utilisateur lance l'application. Si une mise à jour est disponible, elle sera téléchargée et lancée ; sinon, la version existante de l'application sera démarrée.  
  
 Cette stratégie est particulièrement adaptée aux connexions réseau à large bande passante ; le délai nécessaire au lancement de l'application peut être inacceptable sur des connexions à bande passante restreinte.  
  
 Pour activer cette stratégie de mise à jour, cliquez sur **avant le démarrage de l’application** dans les **choisissez à quel moment l’application doit vérifier les mises à jour** section de la **mises à jour de l’Application** boîte de dialogue.  
  
 Cela revient à modifier le **mise à jour** manifeste d’élément dans le déploiement comme suit :  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>Activation de l'option de mise à jour obligatoire  
 Dans certains cas, vous souhaitez obliger les utilisateurs à exécuter une version mise à jour de votre application. Par exemple, vous pouvez apporter une modification à une ressource externe, telle qu'un service Web, qui empêche le fonctionnement correct de la version antérieure de votre application. Dans ce cas, vous souhaitez marquer votre mise à jour comme étant obligatoire et empêcher les utilisateurs d'exécuter la version antérieure.  
  
> [!NOTE]
>  Bien que vous pouvez exiger des mises à jour à l’aide d’autres stratégies de mise à jour, la vérification de la **avant le démarrage de l’application** est le seul moyen de garantir qu’une version plus ancienne ne peut pas être exécutée. Lorsque la mise à jour obligatoire est détectée au démarrage, l'utilisateur doit accepter la mise à jour ou fermer l'application.  
  
 Pour marquer une mise à jour comme requis, cliquez sur **spécifier une version minimale requise pour cette application** dans les **Application met à jour** boîte de dialogue zone, puis spécifiez la version de publication (**majeure**, **Secondaire**, **générer**, **révision**), qui spécifie le numéro de version le plus bas de l’application qui peut être installé.  
  
 Ceci est le même que le **minimumRequiredVersion** attribut de la **déploiement** élément dans le manifeste de déploiement ; par exemple :  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>Spécification d'intervalles de mise à jour  
 Vous pouvez également spécifier la fréquence de vérification des mises à jour de l'application. Pour ce faire, spécifiez l'application devant vérifier les mises à jour après le démarrage comme indiqué dans « Vérification des mises à jour après le démarrage de l'application » plus haut dans cette rubrique.  
  
 Pour spécifier l’intervalle de mise à jour, définissez la **spécifier la fréquence à laquelle l’application doit vérifier les mises à jour** propriétés dans le **mises à jour de l’Application** boîte de dialogue.  
  
 Ceci est le même que le **maximumAge** et **unité** les attributs de la **mise à jour** élément dans le manifeste de déploiement.  
  
 Par exemple, vous pouvez souhaiter une vérification à chaque exécution de l'application, une fois par semaine ou une fois par mois. En l'absence d'une connexion réseau au moment spécifié, la vérification de mises à jour est effectuée à la prochaine exécution de l'application.  
  
## <a name="providing-a-user-interface-for-updates"></a>Présentation d'une interface utilisateur pour les mises à jour  
 Avec cette stratégie, le développeur de l'application fournit une interface utilisateur qui permet à l'utilisateur de choisir le moment ou la fréquence de vérification des mises à jour. Par exemple, vous pouvez fournir une commande "Vérifier les mises à jour maintenant" ou une boîte de dialogue "Paramètres de mise à jour" avec un choix d'intervalles de mise à jour différents. Le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API de déploiement fournissent une infrastructure pour la programmation de votre propre interface utilisateur de mise à jour. Pour plus d'informations, consultez l'espace de noms <xref:System.Deployment.Application>.  
  
 Si votre application utilise des API de déploiement pour contrôler sa propre logique de mise à jour, vous devez bloquer la vérification de la mise à jour comme décrit dans « Blocage de la vérification des mises à jour » dans la section suivante.  
  
 Cette stratégie est spécialement appropriée lorsque vous avez besoin de plusieurs stratégies de mise à jour pour des utilisateurs différents.  
  
## <a name="blocking-update-checking"></a>Blocage de la vérification des mises à jour  
 Il est également possible de faire en sorte que votre application ne vérifie jamais les mises à jour. Par exemple, vous pouvez posséder une application simple qui ne sera jamais mise à jour, mais vous souhaitez profiter de la facilité d'installation fournie par le déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Vous devez également bloquer la vérification de la mise à jour si votre application utilise des API de déploiement pour effectuer ses propres mises à jour ; consultez « Présentation d'une interface utilisateur pour les mises à jour », plus haut dans cette rubrique.  
  
 Pour bloquer la vérification de la mise à jour, désactivez la **l’application doit vérifier les mises à jour** case à cocher dans la boîte de dialogue d’Application des mises à jour.  
  
 Vous pouvez également bloquer la vérification des mises à jour en supprimant la balise `<Subscription>` dans le manifeste de déploiement.  
  
## <a name="permission-elevation-and-updates"></a>Élévation d'autorisations et mises à jour  
 Si une nouvelle version d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] requiert l'exécution d'un niveau de confiance supérieur à la version précédente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] invite l'utilisateur à indiquer s'il souhaite que ce niveau supérieur de confiance soit accordé à l'application. Si l'utilisateur refuse d'accorder le niveau de confiance supérieur, la mise à jour n'est pas installée. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] invitera l'utilisateur à installer de nouveau l'application lors du prochain redémarrage. Si l'utilisateur refuse d'accorder le niveau de confiance supérieur à ce stade et que la mise à jour ne soit pas marquée comme étant obligatoire, l'ancienne version de l'application est exécutée. Toutefois, si la mise à jour est obligatoire, l'application ne sera pas exécutée tant que l'utilisateur n'aura pas accepté le niveau de confiance supérieur.  
  
 Si vous utilisez le déploiement d'applications approuvées, vous ne recevrez aucune invite concernant les niveaux de confiance. Pour plus d'informations, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Deployment.Application>   
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Mises à jour des applications par ClickOnce](../deployment/how-clickonce-performs-application-updates.md)   
 [Guide pratique pour gérer les mises à jour pour une application ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)