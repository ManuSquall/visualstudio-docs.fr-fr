---
title: Création d’Applications ClickOnce pour d’autres pour déployer | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f2b7bb6c990567a483ab28d215019fe1b259d166
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862084"
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Création d'applications ClickOnce destinées à être déployées par des tiers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pas tous les développeurs qui créent des déploiements ClickOnce plan déployer les applications elles-mêmes. Bon nombre d'entre eux simplement empaqueter leur application à l’aide de ClickOnce et ensuite remettre les fichiers à un client, par exemple une grande entreprise. Le client est alors chargé d’héberger l’application sur son réseau. Cette rubrique décrit certains des problèmes inhérents à ces déploiements dans les versions du .NET Framework antérieures à la version 3.5. Elle décrit ensuite une nouvelle solution fournie dans le .NET Framework 3.5 à l’aide de la nouvelle fonctionnalité « utiliser le manifeste pour approbation ». Enfin, elle présente les stratégies recommandées pour la création de déploiements de ClickOnce pour les clients qui utilisent encore des versions antérieures du .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problèmes liés à la création de déploiements pour les clients  
 Plusieurs problèmes se produisent lorsque vous envisagez de fournir un déploiement à un client. Le premier problème concerne la signature de code. Pour être déployés sur un réseau, le manifeste de déploiement et le manifeste d’application d’un déploiement ClickOnce doivent être signés avec un certificat numérique. Cela soulève la question de s’il faut utiliser le certificat du développeur ou celui du client lors de la signature des manifestes.  
  
 La question de certificat à utiliser est critique, comme l’identité d’une application ClickOnce est basée sur la signature numérique du manifeste de déploiement. Si le développeur signe le manifeste de déploiement, il peut provoquer des conflits si le client est une grande entreprise, et plus d’une division de l’entreprise déploie une version personnalisée de l’application.  
  
 Par exemple, supposons que Adventure Works a un service financier et un service des ressources humaines. Les deux services de licence une application ClickOnce à partir de Microsoft Corporation qui génère des rapports à partir des données stockées dans une base de données SQL. Microsoft fournit à chaque service avec une version de l’application qui est adaptée à leurs données. Si les applications sont signées avec le même certificat Authenticode, un utilisateur qui tente d’utiliser les deux applications, une erreur, ClickOnce considérant que la deuxième application comme étant identique à la première. Dans ce cas, le client peut rencontrer des effets secondaires inattendus et indésirables qui incluent la perte de toutes les données stockées localement par l’application.  
  
 Un autre problème lié à la signature du code est le `deploymentProvider` élément dans le manifeste de déploiement, ce qui indique à ClickOnce où rechercher les mises à jour de l’application. Cet élément doit être ajouté au manifeste de déploiement avant la signature. Si cet élément est ajouté par la suite, le manifeste de déploiement doit être signé à nouveau.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Pour signer le manifeste de déploiement par le client  
 Une solution à ce problème de déploiements non unique consiste à avoir le signe de développeur le manifeste d’application et le client signer le manifeste de déploiement. Bien que cette approche fonctionne, il présente d’autres problèmes. Dans la mesure où un certificat Authenticode doive rester protégé, le client ne peut pas donner simplement le certificat au développeur de signer le déploiement. Bien que les clients puissent signer le manifeste de déploiement eux-mêmes à l’aide des outils disponibles gratuitement avec le SDK .NET Framework, cela peut nécessiter des connaissances techniques que le client est en mesure de fournir. Dans ce cas, le développeur crée généralement une application, site Web ou autre mécanisme par lequel le client peut envoyer leur version de l’application pour la signature.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>L’Impact du client de signature sur la sécurité des applications ClickOnce  
 Même si le développeur et le client accepte que le client doit signer le manifeste d’application, cela soulève des autres problèmes qui entourent l’identité d’application, en particulier car il s’applique à un déploiement d’applications approuvées. (Pour plus d’informations sur cette fonctionnalité, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) Supposons qu’Adventure Works souhaite configurer ses ordinateurs clients afin que n’importe quelle application fournie par Microsoft Corporation s’exécute avec une confiance totale. Si Adventure Works signe le manifeste de déploiement, ClickOnce utilise signature de sécurité d’Adventure Work pour déterminer le niveau de confiance de l’application.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Création de déploiements clients à l’aide du manifeste d’Application de confiance  
 ClickOnce dans .NET Framework 3.5 contient une nouvelle fonctionnalité qui permet aux développeurs et aux clients une nouvelle solution pour le scénario de la façon dont les manifestes doivent être signés. Le manifeste d’application ClickOnce prend en charge un nouvel élément nommé `<useManifestForTrust>` qui permet à un développeur d’indiquer que la signature numérique du manifeste d’application qui doit être utilisé pour les décisions d’approbation. Le développeur utilise des outils d’empaquetage ClickOnce, tels que Visual Studio, Mage.exe et MageUI.exe, d’inclure cet élément dans le manifeste d’application, ainsi que d’incorporer de leur nom de serveur de publication et le nom de l’application dans le manifeste.  
  
 Lorsque vous utilisez `<useManifestForTrust>`, le manifeste de déploiement n’a pas d’être signé avec un certificat Authenticode émis par une autorité de certification. Au lieu de cela, elle peut être signée avec ce que l'on appelle un certificat auto-signé. Un certificat auto-signé est généré par le client ou le développeur à l’aide des outils de kit de développement logiciel .NET Framework standard et puis appliqué au manifeste de déploiement en utilisant les outils de déploiement ClickOnce standards. Pour plus d’informations, consultez [Makecert.exe (outil Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 À l’aide d’un certificat auto-signé pour le manifeste de déploiement présente plusieurs avantages. En éliminant la nécessité pour le client obtenir ou créer leur propre certificat Authenticode, `<useManifestForTrust>` simplifie le déploiement du client, tout en permettant au développeur de conserver son identité de personnalisation sur l’application. Le résultat est un ensemble de déploiements signés qui sont plus sûres et ont des identités d’application uniques. Cela élimine le conflit potentiel qui peut se produire à partir du déploiement de la même application à plusieurs clients.  
  
 Pour obtenir des informations détaillées sur la création d’un déploiement de ClickOnce avec `<useManifestForTrust>` activé, consultez [procédure pas à pas : déploiement manuel d’une Application ClickOnce qui est pas exiger nouvelle signature et qui conserve les informations sur le logo](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Fichier manifeste d’Application comment pour Works approbation lors de l’exécution  
 Pour obtenir une meilleure compréhension du fonctionne de l’aide le manifeste d’application pour approbation lors de l’exécution, prenons l’exemple suivant. Une application ClickOnce qui cible le .NET Framework 3.5 est créée par Microsoft. Le manifeste d’application utilise le `<useManifestForTrust>` élément et est signé par Microsoft. Adventure Works signe le manifeste de déploiement à l’aide d’un certificat auto-signé. Adventure Works les clients sont configurés pour approuver toute application signée par Microsoft.  
  
 Lorsqu’un utilisateur clique sur un lien vers le manifeste de déploiement, ClickOnce installe l’application sur l’ordinateur de l’utilisateur. Les informations de certificat et le déploiement identifier identifie de façon unique l’application ClickOnce sur l’ordinateur client. Si l’utilisateur tente d’installer la même application à nouveau à partir d’un emplacement différent, ClickOnce peut utiliser cette identité pour déterminer que l’application existe déjà sur le client.  
  
 Ensuite, ClickOnce examine le certificat Authenticode qui est utilisé pour signer le manifeste d’application, qui détermine le niveau de confiance accordé par ClickOnce. Dans la mesure où Adventure Works a configuré ses clients pour approuver toute application signée par Microsoft, cette application ClickOnce est confiance totale. Pour plus d'informations, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Création de déploiements de clients pour les Versions antérieures  
 Que se passe-t-il si un développeur déploie des applications ClickOnce pour les clients qui utilisent des versions antérieures du .NET Framework ? Les sections suivantes résument plusieurs solutions recommandées, ainsi que les avantages et les inconvénients de chacun d’eux.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Déploiements de connexion pour le compte client  
 Une stratégie de déploiement est destiné aux développeurs de créer un mécanisme pour signer les déploiements pour le compte de leurs clients, à l’aide de la clé privée du client. Cela empêche le développeur d’avoir à gérer les clés privées ou plusieurs packages de déploiement. Le développeur fournit simplement le même déploiement à chaque client. Il incombe au client personnaliser en fonction de leur environnement en utilisant le service de signature.  
  
 L’inconvénient de cette méthode est le temps et les dépenses sont requis pour son implémentation. Bien que ce service peut être généré en utilisant les outils fournis dans le SDK .NET Framework, il ajoute plus de temps de développement pour le cycle de vie du produit.  
  
 Comme indiqué plus haut dans cette rubrique, un autre inconvénient est que la version de chaque client de l’application aura la même identité d’application, ce qui peut provoquer des conflits. S’il s’agit d’un problème, le développeur peut modifier le champ de nom qui est utilisé lors de la génération du manifeste de déploiement pour donner à chaque application un nom unique. Cela crée une identité distincte pour chaque version de l’application et supprimer les éventuels conflits d’identité. Ce champ correspond à la `-Name` argument pour Mage.exe et pour le **nom** champ sur le **nom** onglet de MageUI.exe.  
  
 Par exemple, que le développeur a créé une application nommée Application1. Au lieu de créer un déploiement unique avec le champ de nom défini sur Application1, le développeur peut créer plusieurs déploiements avec une variation spécifique du client sur ce nom, tel que Application1-ClientA, Application1-client b et ainsi de suite.  
  
### <a name="deploy-using-a-setup-package"></a>Déployer à l’aide d’un Package d’installation  
 Une deuxième stratégie de déploiement consiste à générer un projet Microsoft Setup pour effectuer le déploiement initial de l’application ClickOnce. Cela peut être fourni dans un des formats suivants : déploiement MSI, fichier exécutable d’installation (. (EXE), ou dans un fichier CAB (.cab) avec un script de commandes.  
  
 À l’aide de cette technique, le développeur fournit au client un déploiement qui inclut les fichiers d’application, le manifeste d’application et un manifeste de déploiement qui sert de modèle. Le client exécute le programme d’installation, qui vous invite à entrer une URL de déploiement (serveur ou fichier partager l’emplacement à partir duquel les utilisateurs installent l’application ClickOnce), ainsi que d’un certificat numérique. L’application d’installation peut également demander pour les autres options de configuration de ClickOnce, telles que de l’intervalle de vérification de mise à jour. Une fois que ces informations sont collectées, le programme d’installation voulez-vous générer le manifeste de déploiement réel, signez-le et publier l’application ClickOnce à l’emplacement de serveur désigné.  
  
 Il existe trois façons que les clients puissent signer le manifeste de déploiement dans cette situation :  
  
1. Le client peut utiliser un certificat valide émis par une autorité de certification (CA).  
  
2. Une variante de cette approche, le client peut choisir signer le manifeste de déploiement avec un certificat auto-signé. L’inconvénient de cette approche est qu’elle entraîne l’application afficher les mots « Éditeur inconnu » lorsque l’utilisateur est invité s’il faut l’installer. Toutefois, l’avantage est qu’il empêche les clients plus petits de devoir dépenser du temps et l’argent nécessaire pour un certificat émis par une autorité de certification.  
  
3. Enfin, le développeur peut inclure son propre certificat auto-signé dans le package d’installation. Cela introduit des problèmes potentiels avec l’identité d’application décrit précédemment dans cette rubrique.  
  
   L’inconvénient de la méthode de projet de déploiement d’installation est le temps et les dépenses nécessaires pour générer une application de déploiement personnalisé.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Client ont générer un manifeste de déploiement  
 Une troisième stratégie de déploiement est pour transmettre uniquement les fichiers d’application et le manifeste d’application désactivée au client. Dans ce scénario, le client est responsable de l’utilisation du SDK .NET Framework pour générer et signer le manifeste de déploiement.  
  
 L’inconvénient de cette méthode est qu’il nécessite le client pour installer les outils du Kit de développement logiciel .NET Framework et pour qu’un développeur ou un administrateur système qui est de maîtriser parfaitement. Certains clients peuvent rechercher une solution nécessitant peu ou aucune connaissance technique de leur part.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’Applications ClickOnce pour le test et les serveurs de Production sans nouvelle signature](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations relatives à la personnalisation](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)



