---
title: Choix d’une stratégie de mise à jour ClickOnce | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edba26d951afb0ba2215af4c0a0eac09b1c31513
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608489"
---
# <a name="choose-a-clickonce-update-strategy"></a>Choisir une stratégie de mise à jour ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut fournir des mises à jour d’application automatiques. Une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lit périodiquement son fichier manifeste de déploiement pour vérifier si des mises à jour de l’application sont disponibles. Si disponible, la nouvelle version de l'application est téléchargée et exécutée. Pour des raisons d'efficacité, seuls les fichiers modifiés sont téléchargés.

 Lorsque vous concevez une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous devez déterminer quelle stratégie l'application utilisera pour vérifier les mises à jour disponibles. Trois stratégies de base sont possibles : la vérification des mises à jour au démarrage de l'application, la vérification des mises à jour après le démarrage de l'application (exécutée dans un thread d'arrière-plan) ou la présentation d'une interface utilisateur destinée aux mises à jour.

 De plus, vous pouvez déterminer la fréquence de vérification des mises à jour effectuées par l'application et configurer une mise à jour obligatoire.

> [!NOTE]
>  Les mises à jour d'application exigent une connexion au réseau. En l'absence d'une connexion réseau, l'application s'exécute sans vérifier les mises à jour, quelle que soit la stratégie de mise à jour choisie.

> [!NOTE]
>  Dans .NET Framework 2.0 et .NET Framework 3.0, chaque fois que votre application vérifie les mises à jour, avant ou après le démarrage ou à l’aide de la \<xref:System.Deployment.Application > API, vous devez définir `deploymentProvider` dans le manifeste de déploiement. Dans Visual Studio, l’élément `deploymentProvider` correspond au champ **Emplacement de mise à jour** dans la boîte de dialogue **Mises à jour** de l’onglet **Publier**. Cette règle est assouplie dans .NET Framework 3.5. Pour plus d’informations, consultez [déploiement ClickOnce Applications pour de test et les serveurs de Production sans Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

## <a name="check-for-updates-after-application-startup"></a>Recherchez les mises à jour après le démarrage de l’application
 Si vous utilisez cette stratégie, l'application tente de localiser et de lire le fichier manifeste de déploiement en arrière-plan pendant l'exécution de l'application. Si une mise à jour est disponible, lors de la prochaine exécution de l'application, l'utilisateur sera invité à télécharger et à installer la mise à jour.

 Cette stratégie est tout particulièrement adaptée aux connexions réseau à bande passante restreinte ou aux applications plus importantes, susceptibles de nécessiter de longs téléchargements.

 Pour activer cette stratégie de mise à jour, cliquez sur **Après le démarrage de l’application** dans la section **Choisissez à quel moment l’application doit vérifier la disponibilité de mises à jour** de la boîte de dialogue **Mises à jour des applications**. Ensuite, spécifiez un intervalle de mise à jour dans la section **Spécifiez à quelle fréquence l’application doit vérifier la disponibilité de mises à jour**.

 Ceci revient à modifier l’élément **Update** dans le manifeste de déploiement comme suit :

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <expiration maximumAge="6" unit="hours" />
   </update>
</subscription>
```

## <a name="check-for-updates-before-application-startup"></a>Recherchez les mises à jour avant le démarrage de l’application
 La stratégie par défaut est d'essayer de localiser et de lire le fichier manifeste de déploiement avant le démarrage de l'application. Avec cette stratégie, l'application tente de localiser et de lire le fichier manifeste de déploiement chaque fois que l'utilisateur lance l'application. Si une mise à jour est disponible, elle sera téléchargée et lancée ; sinon, la version existante de l'application sera démarrée.

 Cette stratégie est particulièrement adaptée aux connexions réseau à large bande passante ; le délai nécessaire au lancement de l'application peut être inacceptable sur des connexions à bande passante restreinte.

 Pour activer cette stratégie de mise à jour, cliquez sur **Avant le démarrage de l’application** dans la section **Choisissez à quel moment l’application doit vérifier la disponibilité de mises à jour** de la boîte de dialogue **Mises à jour des applications**.

 Ceci revient à modifier l’élément **Update** dans le manifeste de déploiement comme suit :

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <beforeApplicationStartup />
   </update>
</subscription>
```

## <a name="make-updates-required"></a>Vérifiez les mises à jour requises
 Dans certains cas, vous souhaitez obliger les utilisateurs à exécuter une version mise à jour de votre application. Par exemple, vous pouvez apporter une modification à une ressource externe, telle qu'un service Web, qui empêche le fonctionnement correct de la version antérieure de votre application. Dans ce cas, vous souhaitez marquer votre mise à jour comme étant obligatoire et empêcher les utilisateurs d'exécuter la version antérieure.

> [!NOTE]
>  Bien qu’il soit possible d’exiger des mises à jour à l’aide des autres stratégies de mise à jour, la vérification **Avant le démarrage de l’application** est la seule façon d’interdire l’exécution d’une version antérieure. Lorsque la mise à jour obligatoire est détectée au démarrage, l'utilisateur doit accepter la mise à jour ou fermer l'application.

 Pour marquer une mise à jour comme étant obligatoire, cliquez sur **Spécifiez la version minimale requise pour cette application** dans la boîte de dialogue **Mises à jour des applications**, puis spécifiez la version de publication (**Majeure**, **Mineure**, **Build**, **Révision**) qui spécifie le numéro de version minimal de l’application qui peut être installée.

 Ceci revient à définir l’attribut **minimumRequiredVersion** de l’élément **Deployment** dans le manifeste de déploiement. Par exemple :

```xml
<deployment install="true" minimumRequiredVersion="1.0.0.0">
```

## <a name="specify-update-intervals"></a>Spécifier des intervalles de mise à jour
 Vous pouvez également spécifier la fréquence de vérification des mises à jour de l'application. Pour ce faire, spécifiez l'application devant vérifier les mises à jour après le démarrage comme indiqué dans « Vérification des mises à jour après le démarrage de l'application » plus haut dans cette rubrique.

 Pour spécifier l’intervalle de mise à jour, définissez les propriétés **Spécifiez à quelle fréquence l’application doit vérifier la disponibilité de mises à jour** dans la boîte de dialogue **Mises à jour des applications**.

 Ceci revient à définir les attributs **maximumAge** et **unit** de l’élément **Update** dans le manifeste de déploiement.

 Par exemple, vous pouvez souhaiter une vérification à chaque exécution de l'application, une fois par semaine ou une fois par mois. En l'absence d'une connexion réseau au moment spécifié, la vérification de mises à jour est effectuée à la prochaine exécution de l'application.

## <a name="provide-a-user-interface-for-updates"></a>Fournir une interface utilisateur pour les mises à jour
 Avec cette stratégie, le développeur de l'application fournit une interface utilisateur qui permet à l'utilisateur de choisir le moment ou la fréquence de vérification des mises à jour. Par exemple, vous pouvez fournir une commande "Vérifier les mises à jour maintenant" ou une boîte de dialogue "Paramètres de mise à jour" avec un choix d'intervalles de mise à jour différents. Les API de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fournissent une infrastructure pour la programmation de votre propre interface utilisateur de mise à jour. Pour plus d'informations, consultez l'espace de noms <xref:System.Deployment.Application>.

 Si votre application utilise des API de déploiement pour contrôler sa propre logique de mise à jour, vous devez bloquer la vérification de la mise à jour comme décrit dans « Blocage de la vérification des mises à jour » dans la section suivante.

 Cette stratégie est spécialement appropriée lorsque vous avez besoin de plusieurs stratégies de mise à jour pour des utilisateurs différents.

## <a name="block-update-checking"></a>Bloquer la vérification de la mise à jour
 Il est également possible de faire en sorte que votre application ne vérifie jamais les mises à jour. Par exemple, vous pouvez posséder une application simple qui ne sera jamais mise à jour, mais vous souhaitez profiter de la facilité d'installation fournie par le déploiement de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

 Vous devez également bloquer la mise à jour de vérifier si votre application utilise des API de déploiement pour effectuer ses propres mises à jour ; consultez « Fournissent une interface utilisateur pour les mises à jour » plus haut dans cette rubrique.

 Pour bloquer la vérification des mises à jour, désactivez la case à cocher **L’application doit vérifier la disponibilité de mises à jour** dans la boîte de dialogue Mises à jour des applications.

 Vous pouvez également bloquer la vérification des mises à jour en supprimant la balise `<Subscription>` dans le manifeste de déploiement.

## <a name="permission-elevation-and-updates"></a>Élévation d’autorisations et mises à jour
 Si une nouvelle version d'une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] requiert l'exécution d'un niveau de confiance supérieur à la version précédente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] invite l'utilisateur à indiquer s'il souhaite que ce niveau supérieur de confiance soit accordé à l'application. Si l'utilisateur refuse d'accorder le niveau de confiance supérieur, la mise à jour n'est pas installée. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] invitera l’utilisateur à réinstaller l’application lors du prochain redémarrage. Si l'utilisateur refuse d'accorder le niveau de confiance supérieur à ce stade et que la mise à jour ne soit pas marquée comme étant obligatoire, l'ancienne version de l'application est exécutée. Toutefois, si la mise à jour est obligatoire, l'application ne sera pas exécutée tant que l'utilisateur n'aura pas accepté le niveau de confiance supérieur.

 Si vous utilisez le déploiement d'applications approuvées, vous ne recevrez aucune invite concernant les niveaux de confiance. Pour plus d’informations, consultez [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md).

## <a name="see-also"></a>Voir aussi
 \<xref:System.Deployment.Application>
- [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Mises à jour des applications par ClickOnce](../deployment/how-clickonce-performs-application-updates.md)
- [Guide pratique pour gérer les mises à jour pour une application ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)