---
title: Création d’applications ClickOnce destinées à être déployées par d’autres | Microsoft Docs
description: Découvrez les applications ClickOnce hébergées par le client développées dans .NET Framework 3,5 et les versions précédentes du .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7379038d1c2bf203f7787e69408ddd9b2e30f372
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382999"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Créer des applications ClickOnce destinées à être déployées par des tiers
Tous les développeurs qui créent des déploiements ClickOnce ne planifient pas le déploiement des applications elles-mêmes. Un grand nombre d’entre elles empaquetent simplement leur application à l’aide de ClickOnce, puis remet les fichiers à un client, par exemple une grande entreprise. Le client devient celui qui est responsable de l’hébergement de l’application sur son réseau. Cette rubrique décrit certains des problèmes inhérents à ces déploiements dans les versions de .NET Framework antérieures à la version 3,5. Il décrit ensuite une nouvelle solution fournie à l’aide de la nouvelle fonctionnalité « utiliser le manifeste pour l’approbation » dans le .NET Framework 3,5. Enfin, il conclut par des stratégies recommandées pour la création de déploiements ClickOnce pour les clients qui utilisent encore des versions antérieures du .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problèmes liés à la création de déploiements pour les clients
 Plusieurs problèmes se produisent lorsque vous envisagez de fournir un déploiement à un client. Le premier problème concerne la signature du code. Pour être déployé sur un réseau, le manifeste de déploiement et le manifeste d’application d’un déploiement ClickOnce doivent tous deux être signés avec un certificat numérique. Cela soulève la question de savoir s’il faut utiliser le certificat du développeur ou le certificat du client lors de la signature des manifestes.

 La question du certificat à utiliser est critique, car l’identité d’une application ClickOnce est basée sur la signature numérique du manifeste de déploiement. Si le développeur signe le manifeste de déploiement, cela peut entraîner des conflits si le client est une grande entreprise et que plusieurs divisions de l’entreprise déploient une version personnalisée de l’application.

 Par exemple, imaginons qu’Adventure Works possède un service financier et un service des ressources humaines. Les deux services possèdent une licence ClickOnce de Microsoft Corporation qui génère des rapports à partir des données stockées dans une base de données SQL. Microsoft fournit à chaque service une version de l’application qui est personnalisée pour ses données. Si les applications sont signées avec le même certificat Authenticode, un utilisateur qui tente d’utiliser les deux applications rencontrerait une erreur, car ClickOnce considère que la deuxième application est identique à la première. Dans ce cas, le client peut rencontrer des effets secondaires imprévisibles et indésirables qui incluent la perte de toutes les données stockées localement par l’application.

 Un autre problème lié à la signature de code est l' `deploymentProvider` élément dans le manifeste de déploiement, qui indique à ClickOnce où rechercher des mises à jour d’application. Cet élément doit être ajouté au manifeste de déploiement avant d’être signé. Si cet élément est ajouté par la suite, le manifeste de déploiement doit être à nouveau signé.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Exiger que le client signe le manifeste de déploiement
 L’une des solutions à ce problème de déploiements non uniques consiste à demander au développeur de signer le manifeste de l’application, et le client signe le manifeste de déploiement. Bien que cette approche fonctionne, elle introduit d’autres problèmes. Étant donné qu’un certificat Authenticode doit rester un élément multimédia protégé, le client ne peut pas simplement fournir le certificat au développeur pour signer le déploiement. Alors que le client peut signer le manifeste de déploiement à l’aide d’outils librement disponibles avec le kit de développement logiciel (SDK) .NET Framework, cela peut nécessiter des connaissances techniques supplémentaires que le client est prêt ou en mesure de fournir. Dans ce cas, le développeur crée généralement une application, un site Web ou un autre mécanisme par le biais duquel le client peut envoyer sa version de l’application pour la signature.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Impact de la signature client sur la sécurité des applications ClickOnce
 Même si le développeur et le client conviennent que le client doit signer le manifeste de l’application, cela soulève d’autres problèmes qui entourent l’identité de l’application, en particulier s’il s’applique au déploiement d’applications approuvées. (Pour plus d’informations sur cette fonctionnalité, consultez [vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md).) Disons qu’Adventure Works souhaite configurer ses ordinateurs clients de sorte que toute application qui leur est fournie par Microsoft Corporation s’exécute avec une confiance totale. Si Adventure Works signe le manifeste de déploiement, ClickOnce utilise la signature de sécurité de Adventure Work pour déterminer le niveau de confiance de l’application.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Créer des déploiements clients à l’aide du manifeste d’application pour l’approbation
 ClickOnce dans le .NET Framework 3,5 contient une nouvelle fonctionnalité qui offre aux développeurs et aux clients une nouvelle solution dans le scénario de signature des manifestes. Le manifeste d’application ClickOnce prend en charge un nouvel élément nommé `<useManifestForTrust>` qui permet à un développeur de signifier que la signature numérique du manifeste d’application est ce qui doit être utilisé pour prendre des décisions d’approbation. Le développeur utilise les outils d’empaquetage ClickOnce, tels que *Mage.exe* , *MageUI.exe* et Visual Studio, pour inclure cet élément dans le manifeste de l’application, ainsi que pour incorporer à la fois son nom d’éditeur et le nom de l’application dans le manifeste.

 Lors de l’utilisation de `<useManifestForTrust>` , le manifeste de déploiement n’a pas besoin d’être signé avec un certificat Authenticode émis par une autorité de certification. Au lieu de cela, il peut être signé avec ce qui est connu sous le nom de certificat auto-signé. Un certificat auto-signé est généré par le client ou par le développeur à l’aide des outils du kit de développement logiciel (SDK) standard .NET Framework, puis appliqué au manifeste de déploiement à l’aide des outils de déploiement ClickOnce standard. Pour plus d’informations, consultez [Makecert](/windows/desktop/SecCrypto/makecert).

 L’utilisation d’un certificat auto-signé pour le manifeste de déploiement présente plusieurs avantages. En éliminant la nécessité pour le client d’obtenir ou de créer son propre certificat Authenticode, `<useManifestForTrust>` simplifie le déploiement du client, tout en permettant au développeur de conserver sa propre identité de personnalisation sur l’application. Le résultat est un ensemble de déploiements signés plus sûrs et ayant des identités d’application uniques. Cela élimine le conflit potentiel qui peut se produire lors du déploiement de la même application sur plusieurs clients.

 Pour obtenir des informations pas à pas sur la création d’un déploiement ClickOnce avec `<useManifestForTrust>` activé, consultez [procédure pas à pas : déployer manuellement une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations de personnalisation](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Fonctionnement du manifeste d’application pour l’approbation au moment de l’exécution
 Pour obtenir une meilleure compréhension de la façon dont l’utilisation du manifeste d’application pour l’approbation fonctionne au moment de l’exécution, examinez l’exemple suivant. Une application ClickOnce qui cible le .NET Framework 3,5 est créée par Microsoft. Le manifeste d’application utilise l' `<useManifestForTrust>` élément et est signé par Microsoft. Adventure Works signe le manifeste de déploiement à l’aide d’un certificat auto-signé. Les clients Adventure Works sont configurés pour approuver toute application signée par Microsoft.

 Lorsqu’un utilisateur clique sur un lien vers le manifeste de déploiement, ClickOnce installe l’application sur l’ordinateur de l’utilisateur. Le certificat et les informations de déploiement identifient l’application de façon unique sur l’ordinateur client. Si l’utilisateur tente à nouveau d’installer la même application à partir d’un autre emplacement, ClickOnce peut utiliser cette identité pour déterminer que l’application existe déjà sur le client.

 Ensuite, ClickOnce examine le certificat Authenticode utilisé pour signer le manifeste de l’application, qui détermine le niveau de confiance accordé par ClickOnce. Dans la mesure où Adventure Works a configuré ses clients pour qu’ils approuvent toute application signée par Microsoft, cette application ClickOnce bénéficie d’une confiance totale. Pour plus d’informations, consultez [vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Créer des déploiements clients pour des versions antérieures
 Que se passe-t-il si un développeur déploie des applications ClickOnce pour des clients qui utilisent des versions antérieures du .NET Framework ? Les sections suivantes résument plusieurs solutions recommandées, ainsi que les avantages et les inconvénients de chacune d’elles.

### <a name="sign-deployments-on-behalf-of-customer"></a>Signer les déploiements pour le compte du client
 Une stratégie de déploiement possible est que le développeur crée un mécanisme de signature des déploiements pour le compte de ses clients, à l’aide de la clé privée du client. Cela empêche le développeur de devoir gérer des clés privées ou plusieurs packages de déploiement. Le développeur fournit simplement le même déploiement à chaque client. Il revient au client de le personnaliser pour son environnement à l’aide du service de signature.

 L’inconvénient de cette méthode est le temps et les dépenses requis pour l’implémenter. Bien qu’un tel service puisse être créé à l’aide des outils fournis dans le kit de développement logiciel (SDK) .NET Framework, il augmentera le temps de développement du cycle de vie du produit.

 Comme indiqué précédemment dans cette rubrique, l’inconvénient est que la version de l’application de chaque client aura la même identité d’application, ce qui peut entraîner des conflits. Si cela pose problème, le développeur peut modifier le champ nom utilisé lors de la génération du manifeste de déploiement pour attribuer un nom unique à chaque application. Cela permet de créer une identité distincte pour chaque version de l’application et d’éliminer les conflits d’identité potentiels. Ce champ correspond à l' `-Name` argument pour Mage.exe et au champ **nom** sous l’onglet **nom** dans MageUI.exe.

 Par exemple, imaginons que le développeur a créé une application nommée Application1. Au lieu de créer un déploiement unique avec le champ Name défini sur Application1, le développeur peut créer plusieurs déploiements avec une variation spécifique au client sur ce nom, par exemple Application1-ClientA, Application1-CustomerB, et ainsi de suite.

### <a name="deploy-using-a-setup-package"></a>Déployer à l’aide d’un package d’installation
 Une deuxième stratégie de déploiement possible consiste à générer un projet d’installation Microsoft pour effectuer le déploiement initial de l’application ClickOnce. Il peut être fourni dans l’un des différents formats suivants : en tant que déploiement MSI, en tant qu’exécutable d’installation (. EXE), ou en tant que fichier cabinet (. cab) avec un script de commandes.

 À l’aide de cette technique, le développeur fournit au client un déploiement qui comprend les fichiers d’application, le manifeste d’application et un manifeste de déploiement qui sert de modèle. Le client exécute le programme d’installation, ce qui l’invite à entrer une URL de déploiement (le serveur ou l’emplacement du partage de fichiers à partir duquel les utilisateurs installent l’application ClickOnce), ainsi qu’un certificat numérique. L’application d’installation peut également choisir d’inviter des options de configuration ClickOnce supplémentaires, telles que l’intervalle de vérification des mises à jour. Une fois ces informations collectées, le programme d’installation génère le manifeste de déploiement réel, le signe et publie l’application ClickOnce à l’emplacement du serveur désigné.

 Le client peut signer le manifeste de déploiement de trois façons :

1. Le client peut utiliser un certificat valide émis par une autorité de certification (CA).

2. En guise de variation sur cette approche, le client peut choisir de signer son manifeste de déploiement avec un certificat auto-signé. L’inconvénient de cette opération est que l’application affiche les mots « éditeur inconnu » lorsque l’utilisateur est invité à indiquer s’il faut l’installer. Toutefois, l’avantage est qu’il empêche les clients plus petits d’avoir à consacrer le temps et l’argent requis pour un certificat émis par une autorité de certification.

3. Enfin, le développeur peut inclure son propre certificat auto-signé dans le package d’installation. Cela introduit les problèmes potentiels liés à l’identité de l’application abordée précédemment dans cette rubrique.

   L’inconvénient de la méthode du projet de déploiement de l’installation est le temps et les dépenses nécessaires à la création d’une application de déploiement personnalisée.

### <a name="have-customer-generate-deployment-manifest"></a>Demander au client de générer un manifeste de déploiement
 Une troisième stratégie de déploiement possible consiste à transmettre uniquement les fichiers d’application et le manifeste d’application au client. Dans ce scénario, le client est responsable de l’utilisation du kit de développement logiciel (SDK) .NET Framework pour générer et signer le manifeste de déploiement.

 L’inconvénient de cette méthode est qu’elle exige que le client installe les outils du kit de développement logiciel (SDK) .NET Framework et qu’il dispose d’un développeur ou d’un administrateur système compétent pour les utiliser. Certains clients peuvent demander une solution nécessitant peu ou aucun effort technique de leur part.

## <a name="see-also"></a>Voir aussi
- [Déployer des applications ClickOnce pour des serveurs de test et de production sans avoir à vous reconnecter](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Procédure pas à pas : déploiement manuel d’une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations relatives à la personnalisation](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)