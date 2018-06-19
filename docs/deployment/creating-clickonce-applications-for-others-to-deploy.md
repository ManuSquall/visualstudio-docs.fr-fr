---
title: Création d’Applications ClickOnce pour les autres pour déployer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd6808ac38a67146e53438e5b8f6dc0e07fd0bc5
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34065076"
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Création d'applications ClickOnce destinées à être déployées par des tiers
Envisagez de pas tous les développeurs qui créent des déploiements ClickOnce déployer les applications elles-mêmes. Bon nombre d'entre elles simplement empaqueter leur application à l’aide de ClickOnce et ensuite remettre les fichiers à un client, par exemple une grande entreprise. Le client est alors chargé d’héberger l’application sur son réseau. Cette rubrique décrit certains des problèmes inhérents à ces déploiements dans les versions du .NET Framework antérieures à la version 3.5. Elle décrit ensuite une nouvelle solution fournie dans le .NET Framework 3.5 à l’aide de la nouvelle fonctionnalité « utiliser le manifeste pour approbation ». Enfin, elle présente les stratégies recommandées pour la création de déploiements de ClickOnce pour les clients qui utilisent encore des versions antérieures du .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problèmes liés à la création de déploiements pour les clients  
 Plusieurs problèmes se produisent lorsque vous envisagez de fournir un déploiement à un client. Le premier concerne la signature de code. Afin d’être déployé sur un réseau, le manifeste de déploiement et manifeste d’application d’un déploiement ClickOnce doivent tous deux être signées avec un certificat numérique. Cela pose la question s’il faut utiliser le certificat du développeur ou celui du client lors de la signature des manifestes.  
  
 La question du certificat à utiliser est critique, comme les identités d’une application ClickOnce sont basée sur la signature numérique du manifeste de déploiement. Si le développeur signe le manifeste de déploiement, il peut provoquer des conflits si le client est une grande entreprise, et plus d’une division de l’entreprise déploie une version personnalisée de l’application.  
  
 Par exemple, supposons que Adventure Works a un service financier et service des ressources humaines. Les deux services de licence une application ClickOnce à partir de Microsoft Corporation qui génère des rapports à partir des données stockées dans une base de données SQL. Microsoft fournit à chaque service avec une version de l’application qui est personnalisée pour leurs données. Si les applications sont signées avec le même certificat Authenticode, un utilisateur qui tente d’utiliser les deux applications, une erreur, ClickOnce considérant que la deuxième application est identique à la première. Dans ce cas, le client peut rencontrer des effets inattendus et indésirables qui incluent la perte de toutes les données stockées localement par l’application.  
  
 Un autre problème lié à la signature du code est le `deploymentProvider` élément dans le manifeste de déploiement, ce qui indique à ClickOnce où rechercher des mises à jour de l’application. Cet élément doit être ajouté au manifeste de déploiement avant la signature. Si cet élément est ajouté par la suite, le manifeste de déploiement doit être signé à nouveau.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Le client signer le manifeste de déploiement  
 Une solution à ce problème de déploiements non unique doit avoir le signe de développeur le manifeste d’application et le client signer le manifeste de déploiement. Bien que cette approche fonctionne, il présente d’autres problèmes. Dans la mesure où un certificat Authenticode doit rester protégé, le client ne peut pas simplement remettre le certificat au développeur pour signer le déploiement. Alors que le client peut signer le manifeste de déploiement eux-mêmes à l’aide des outils disponibles gratuitement avec le Kit de développement logiciel .NET Framework, cette opération peut nécessiter des connaissances techniques que le client est en mesure de fournir. Dans ce cas, le développeur crée généralement une application, site Web ou un autre mécanisme par lequel le client peut envoyer leur version de l’application pour la signature.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>L’Impact de la signature sur la sécurité de l’Application ClickOnce par le client  
 Même si le développeur et le client accepte que le client doit signer le manifeste d’application, cela déclenche les autres problèmes qui entourent l’identité de l’application, en particulier quand elle s’applique au déploiement d’applications approuvées. (Pour plus d’informations sur cette fonctionnalité, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) Supposons qu’Adventure Works souhaite configurer ses ordinateurs clients afin que n’importe quelle application fournie par Microsoft Corporation s’exécute avec une confiance totale. Si Adventure Works signe le manifeste de déploiement, ClickOnce utilisera des signatures de sécurité du travail Adventure pour déterminer le niveau de confiance de l’application.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Création de déploiements clients à l’aide du manifeste d’Application de confiance  
 ClickOnce dans le .NET Framework 3.5 contient une nouvelle fonctionnalité qui permet aux développeurs et aux clients une nouvelle solution pour le scénario de la façon dont les manifestes doivent être signés. Le manifeste d’application ClickOnce prend en charge un nouvel élément nommé `<useManifestForTrust>` qui permet à un développeur d’indiquer que la signature numérique du manifeste d’application doit être utilisée pour prendre des décisions d’approbation. Le développeur utilise des outils d’empaquetage ClickOnce, tels que Visual Studio, Mage.exe et MageUI.exe, d’inclure cet élément dans le manifeste d’application, ainsi que pour incorporer leur nom de serveur de publication et le nom de l’application dans le manifeste.  
  
 Lorsque vous utilisez `<useManifestForTrust>`, le manifeste de déploiement n’a pas d’être signé avec un certificat Authenticode émis par une autorité de certification. Au lieu de cela, il peut être signé avec ce que l'on appelle un certificat auto-signé. Un certificat auto-signé est généré par le client ou le développeur à l’aide des outils de développement .NET Framework SDK standard et puis appliqué au manifeste de déploiement en utilisant les outils de déploiement ClickOnce standards. Pour plus d’informations, consultez [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx).  
  
 À l’aide d’un certificat auto-signé pour le manifeste de déploiement présente plusieurs avantages. En éliminant la nécessité pour le client obtenir ou créer son propre certificat Authenticode, `<useManifestForTrust>` simplifie le déploiement pour le client, tout en permettant au développeur de conserver son identité de personnalisation sur l’application. Le résultat est un ensemble de déploiements signés qui sont plus sécurisées et a une identité d’application unique. Cela élimine le conflit potentiel qui peut se produire du déploiement de la même application à plusieurs clients.  
  
 Pour obtenir des informations détaillées sur la création d’un déploiement de ClickOnce avec `<useManifestForTrust>` , consultez [procédure pas à pas : déploiement manuel d’une Application ClickOnce qui est non nécessitent nouvelle signature et qui conserve les informations sur le logo](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Manifeste d’Application de comment pour les travaux d’approbation lors de l’exécution  
 Pour obtenir une meilleure compréhension du fonctionne d’à l’aide du manifeste d’application de confiance lors de l’exécution, prenons l’exemple suivant. Une application ClickOnce qui cible le .NET Framework 3.5 est créée par Microsoft. Le manifeste d’application utilise le `<useManifestForTrust>` élément et est signé par Microsoft. Adventure Works signe le manifeste de déploiement à l’aide d’un certificat auto-signé. Adventure Works, les clients sont configurés pour approuver toute application signée par Microsoft.  
  
 Lorsqu’un utilisateur clique sur un lien vers le manifeste de déploiement, ClickOnce installe l’application sur l’ordinateur de l’utilisateur. Les informations de certificat et de déploiement identifier identifie de façon unique l’application ClickOnce sur l’ordinateur client. Si l’utilisateur tente d’installer à nouveau de la même application à partir d’un emplacement différent, ClickOnce peut utiliser cette identité pour déterminer que l’application existe déjà sur le client.  
  
 Ensuite, ClickOnce examine le certificat Authenticode qui est utilisé pour signer le manifeste d’application, qui détermine le niveau de confiance accordé par ClickOnce. Adventure Works a configuré ses clients pour approuver toute application signée par Microsoft, cette application ClickOnce est de confiance totale. Pour plus d'informations, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Création de déploiements de clients pour les Versions antérieures  
 Que se passe-t-il si un développeur déploie des applications ClickOnce pour les clients qui utilisent des versions antérieures du .NET Framework ? Les sections suivantes résument plusieurs solutions recommandées, ainsi que les avantages et les inconvénients de chacune.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Signature des déploiements pour le compte client  
 Une stratégie de déploiement est destiné aux développeurs de créer un mécanisme pour signer des déploiements pour le compte de leurs clients, à l’aide de la clé privée du client. Cela empêche le développeur d’avoir à gérer les clés privées ou plusieurs packages de déploiement. Le développeur fournit simplement le même déploiement à chaque client. Il incombe au client de personnaliser en fonction de leur environnement en utilisant le service de signature.  
  
 L’inconvénient de cette méthode est le temps et les dépenses qui sont requis pour l’implémenter. Alors que ce service peut être généré à l’aide des outils fournis dans le Kit de développement logiciel .NET Framework, il ajoute plus de temps de développement pour le cycle de vie du produit.  
  
 Comme indiqué plus haut dans cette rubrique, un autre inconvénient est que la version de chaque client de l’application aura la même identité d’application, ce qui peut provoquer des conflits. S’il s’agit d’un problème, le développeur peut modifier le champ nom qui est utilisé lors de la génération du manifeste de déploiement pour donner un nom unique à chaque application. Cela créera une identité distincte pour chaque version de l’application et éliminer les conflits d’identité. Ce champ correspond à la `-Name` argument dans Mage.exe et à la **nom** champ sur la **nom** onglet dans MageUI.exe.  
  
 Par exemple, que le développeur a créé une application nommée Application1. Au lieu de créer un déploiement unique avec le champ de nom défini sur Application1, le développeur peut créer plusieurs déploiements avec une variation spécifiques au client sur ce nom, tel que Application1-ClientA, Application1-ClientB et ainsi de suite.  
  
### <a name="deploy-using-a-setup-package"></a>Déployer à l’aide d’un Package d’installation  
 Une deuxième stratégie de déploiement doit générer un projet Microsoft Setup pour effectuer le déploiement initial de l’application ClickOnce. Cela peut être fourni dans un des formats suivants : déploiement MSI, fichier exécutable d’installation (. (EXE), ou sous la forme d’un fichier CAB (.cab) avec un script de commandes.  
  
 À l’aide de cette technique, le développeur fournit au client un déploiement qui inclut les fichiers d’application, le manifeste d’application et un manifeste de déploiement qui sert de modèle. Le client exécute le programme d’installation, qui vous invite à entrer une URL de déploiement (serveur ou emplacement à partir duquel les utilisateurs installent l’application ClickOnce de partage de fichiers), ainsi que d’un certificat numérique. L’application d’installation peut également choisir d’inviter à entrer les options de configuration ClickOnce supplémentaires, telles que de l’intervalle de vérification de mise à jour. Une fois que ces informations sont collectées, le programme d’installation serait générer le manifeste de déploiement réel, signer et publier l’application ClickOnce à l’emplacement du serveur désigné.  
  
 Il existe trois façons que le client peut signer le manifeste de déploiement dans cette situation :  
  
1.  Le client peut utiliser un certificat valide émis par une autorité de certification (CA).  
  
2.  Une variante de cette approche, le client peut choisir signer le manifeste de déploiement avec un certificat auto-signé. L’inconvénient de cette approche est qu’elle entraîne l’application afficher les mots « Éditeur inconnu » lorsque l’utilisateur est invité à s’il faut l’installer. Toutefois, l’avantage est que les clients plus petits de devoir dépenser du temps et l’argent nécessaire pour un certificat émis par une autorité de certification.  
  
3.  Enfin, le développeur peut inclure son propre certificat auto-signé dans le package d’installation. Cet article présente des problèmes potentiels avec l’identité de l’application décrite précédemment dans cette rubrique.  
  
 L’inconvénient de la méthode de projet de déploiement d’installation est le temps et les dépenses nécessaires à la génération d’une application de déploiement personnalisée.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Avoir client générer le manifeste de déploiement  
 Une stratégie de déploiement tiers est transférer uniquement les fichiers d’application et le manifeste d’application désactivée pour le client. Dans ce scénario, le client est responsable de l’utilisation du SDK .NET Framework pour générer et signer le manifeste de déploiement.  
  
 L’inconvénient de cette méthode est qu’elle requiert le client pour installer les outils de développement .NET Framework SDK et qu’un développeur ou un administrateur système qui est en utilisant les. Certains clients peuvent rechercher une solution nécessitant peu ou aucune connaissance technique de leur part.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’Applications ClickOnce pour les tests et les serveurs de Production sans nouvelle signature](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)   
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations relatives à la personnalisation](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)