---
title: "Creating ClickOnce Applications for Others to Deploy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "preserved branding information"
  - "useManifestForTrust element"
  - "customer deployments [ClickOnce]"
  - "multiple ClickOnce deployment and branding"
  - "ClickOnce applications, previous .NET Framework versions"
  - "application manifests [ClickOnce]"
  - "<useManifestForTrust> element"
  - "manifests [ClickOnce]"
  - "trust applications, ClickOnce"
  - "ClickOnce applications, deployed by others"
  - "ClickOnce applications, previous .NET Framework"
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Creating ClickOnce Applications for Others to Deploy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les développeurs qui créent des déploiements ClickOnce ne comptent pas tous déployer eux\-mêmes les applications.  Nombre d'entre eux se contentent d'empaqueter leur application à l'aide de ClickOnce puis confient les fichiers à un client, comme une grande entreprise.  Le client est alors responsable de l'hébergement de l'application sur son réseau.  Cette rubrique aborde quelques\-uns des problèmes inhérents à ces déploiements dans les versions du .NET Framework antérieures à la version 3.5.  Elle décrit ensuite une nouvelle solution qui consiste à faire appel à la nouvelle fonctionnalité Utiliser le manifeste d'application pour les informations d'approbation de .NET Framework 3.5.  Enfin, elle présente les stratégies recommandées pour la création de déploiements ClickOnce destinés à des clients qui utilisent encore d'anciennes versions du .NET Framework.  
  
## Problèmes associés à la création de déploiements destinés à des clients  
 Plusieurs problèmes se posent lorsque vous projetez de confier un déploiement à un client.  Le premier concerne la signature de code.  Pour être déployés sur un réseau, le manifeste de déploiement et le manifeste d'application d'un déploiement ClickOnce doivent être signés avec un certificat numérique.  La question est de savoir s'il faut utiliser le certificat du développeur ou celui du client lors de la signature des manifestes.  
  
 Cette question est primordiale dans la mesure où l'identité d'une application ClickOnce est basée sur la signature numérique du manifeste de déploiement.  Si le développeur signe le manifeste de déploiement, des conflits peuvent survenir si le client est une grande société dont plusieurs divisions déploient une version personnalisée de l'application.  
  
 Prenons l'exemple de la société Adventure Works qui possède un service financier et un service des ressources humaines.  Ces deux services utilisent une application ClickOnce sous licence de Microsoft Corporation qui génère des rapports à partir de données stockées dans une base de données SQL.  Microsoft fournit à chacun des services une version de l'application qui est personnalisée en fonction de leurs données.  Si les applications sont signées avec le même certificat Authenticode et qu'un utilisateur essaie d'utiliser les deux applications, une erreur est générée, ClickOnce considérant que la deuxième application est identique à la première.  Dans ce cas, des effets secondaires indésirables et imprévisibles risquent de survenir, comme la perte de données stockées localement par l'application.  
  
 L'élément `deploymentProvider` du manifeste de déploiement qui indique à ClickOnce où rechercher des mises à jour d'application constitue un autre problème en matière de signature de code.  Cet élément doit être ajouté au manifeste de déploiement avant la signature,  sinon le manifeste de déploiement doit être de nouveau signé.  
  
### Signature du manifeste de déploiement par le client  
 Pour résoudre le problème posé en cas de multiples déploiements, il est possible de faire signer le manifeste d'application par le développeur et le manifeste de déploiement par le client.  Bien qu'efficace, cette approche introduit d'autres problèmes.  Le certificat Authenticode devant rester protégé, le client ne peut pas simplement remettre le certificat au développeur pour signer le déploiement.  Bien que le Kit de développement .NET Framework SDK propose au client des outils lui permettant de signer lui\-même le manifeste de déploiement, il est possible qu'il ne dispose pas des connaissances techniques suffisantes pour effectuer cette opération ou qu'il souhaite faire appel à une solution moins complexe.  Dans pareils cas, le développeur crée généralement une application, un site Web ou tout autre mécanisme permettant au client de soumettre sa version de l'application à des fins de signature.  
  
### Impact sur la sécurité des applications ClickOnce en cas de signature par le client  
 Même si le développeur et le client acceptent que ce dernier signe le manifeste d'application, d'autres problèmes relatifs à l'identité de l'application se présentent, notamment en termes de déploiement d'applications approuvées.  Consultez [Vue d'ensemble du déploiement d'applications approuvées](../deployment/trusted-application-deployment-overview.md) pour plus d'informations sur cette fonctionnalité. Supposons qu'Adventure Works configure ses ordinateurs clients afin que les applications fournies par Microsoft Corporation soient exécutées avec un niveau de confiance totale.  Si Adventure Works signe le manifeste de déploiement, ClickOnce utilisera la signature de sécurité d'Adventure Work's pour déterminer le niveau de confiance de l'application.  
  
## Création de déploiements clients à l'aide du manifeste d'application pour les informations d'approbation  
 Dans .NET Framework 3.5, ClickOnce contient une nouvelle fonctionnalité qui permet aux développeurs et aux clients de signer les manifestes.  Le manifeste d'application ClickOnce prend en charge le nouvel élément `<useManifestForTrust>` qui permet à un développeur d'indiquer que la signature numérique du manifeste d'application doit être utilisée pour prendre des décisions d'approbation.  Le développeur utilise des outils d'empaquetage ClickOnce, tels que Mage.exe, MageUI.exe et Visual Studio, pour intégrer cet élément au manifeste d'application et incorporer son nom Publisher et le nom de l'application dans le manifeste.  
  
 En cas d'utilisation de `<useManifestForTrust>`, le manifeste de déploiement n'a pas besoin d'être signé avec un certificat Authenticode publié par une autorité de certification.  Il peut être signé avec un certificat auto\-signé.  Le client ou le développeur génère un certificat auto\-signé à l'aide des outils standard du Kit de développement .NET Framework SDK avant de l'appliquer au manifeste de déploiement à l'aide des outils de déploiement ClickOnce standard.  Pour plus d'informations, consultez [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md).  
  
 L'utilisation d'un certificat auto\-signé pour le manifeste de déploiement présente plusieurs avantages.  Comme le client n'a plus besoin d'obtenir ni de créer son propre certificat Authenticode, `<useManifestForTrust>` simplifie le déploiement pour le client et permet au développeur de conserver son identité de personnalisation sur l'application.  Les déploiements signés sont donc mieux sécurisés et possèdent des identités d'application uniques.  En outre, le conflit qui risque de se produire lors du déploiement de la même application pour plusieurs clients est éliminé.  
  
 Pour plus d'informations pas à pas sur la création d'un déploiement ClickOnce avec `<useManifestForTrust>`, consultez [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### Fonctionnement du manifeste d'application pour les informations d'approbation pendant l'exécution  
 Pour mieux comprendre comment le manifeste d'application pour les informations d'approbation fonctionne pendant l'exécution, examinons l'exemple suivant.  Une application ClickOnce ciblant .NET Framework 3.5 est créée par Microsoft.  Le manifeste d'application utilise l'élément `<useManifestForTrust>` et est signé par Microsoft.  Adventure Works signe le manifeste de déploiement à l'aide d'un certificat auto\-signé.  Les clients d'Adventure Works sont configurés pour approuver toute application signée par Microsoft.  
  
 Lorsqu'un utilisateur clique sur un lien vers le manifeste de déploiement, ClickOnce installe l'application sur l'ordinateur de l'utilisateur.  Les informations de certificat et de déploiement permettent à ClickOnce d'identifier l'application de manière unique sur l'ordinateur client.  Si l'utilisateur essaie à nouveau d'installer la même application à partir d'un emplacement différent, ClickOnce peut utiliser cette identité pour déterminer que l'application existe déjà sur le client.  
  
 Ensuite, ClickOnce examine le certificat Authenticode utilisé pour signer le manifeste d'application qui détermine le niveau de confiance accordé par ClickOnce.  Comme Adventure Works a configuré ses clients pour approuver toute application signée par Microsoft, un niveau de confiance totale est accordée à cette application ClickOnce.  Pour plus d'informations, consultez [Vue d'ensemble du déploiement d'applications approuvées](../deployment/trusted-application-deployment-overview.md).  
  
## Création de déploiements clients pour les versions antérieures  
 Que se passe\-t\-il si un développeur déploie des applications ClickOnce pour des clients qui utilisent d'anciennes versions du .NET Framework ?  Les sections suivantes résument plusieurs solutions recommandées, ainsi que les avantages et inconvénients de chacune d'elles.  
  
### Signature des déploiements au nom du client  
 Le développeur peut mettre au point un mécanisme visant à signer des déploiements au nom du client à l'aide de la clé privée de ce dernier.  Cela évite au développeur de gérer les clés privées ou plusieurs packages de déploiement.  Il lui suffit de fournir le même déploiement à chaque client.  Le client n'a plus qu'à le personnaliser en fonction de son environnement en utilisant le service de signature.  
  
 L'inconvénient de cette méthode est que son implémentation est longue et coûteuse.  Bien qu'il puisse être créé à l'aide des outils fournis dans le Kit de développement .NET Framework SDK, ce type de service augmente le temps nécessaire au développement du cycle de vie du produit.  
  
 Comme indiqué précédemment dans cette rubrique, l'autre inconvénient est que la version de l'application de chaque client aura la même identité, ce qui peut engendrer des conflits.  Si ce problème se pose, le développeur peut modifier le champ Nom utilisé lors de la génération du manifeste de déploiement pour donner un nom unique à chaque application.  Chaque version de l'application aura alors sa propre identité et les conflits d'identité disparaîtront.  Ce champ correspond à l'argument `-Name` dans Mage.exe et au champ **Nom** de l'onglet **Nom** dans MageUI.exe.  
  
 Supposons, par exemple, que le développeur a créé une application nommée Application1.  Au lieu de créer un déploiement unique avec le champ Nom défini sur Application1, le développeur peut créer plusieurs déploiements avec une variation de nom spécifique au client, telle que Application1\-ClientA, Application1\-ClientB, et ainsi de suite.  
  
### Déploiement à l'aide d'un package d'installation  
 Une deuxième stratégie de déploiement consiste à générer un projet d'installation Microsoft pour effectuer le déploiement initial de l'application ClickOnce.  Ce projet peut être fourni dans les formats suivants : déploiement MSI, fichier exécutable d'installation \(.EXE\)ou fichier CAB \(.cab\) avec un script de commandes par lot.  
  
 À l'aide de cette technique, le développeur fournit au client un déploiement qui inclut les fichiers d'application, le manifeste d'application et un manifeste de déploiement qui sert de modèle.  Le client exécute le programme d'installation qui l'invite à entrer une URL de déploiement \(serveur ou emplacement de partage de fichiers où les utilisateurs installent l'application ClickOnce\), ainsi qu'un certificat numérique.  L'application d'installation peut également demander au client de spécifier des options de configuration ClickOnce supplémentaires, comme l'intervalle entre vérifications des mises à jour.  Une fois ces informations rassemblées, le programme d'installation génère le vrai manifeste de déploiement, le signe et publie l'application ClickOnce à l'emplacement de serveur désigné.  
  
 Dans cette situation, le client peut signer le manifeste de déploiement de trois façons :  
  
1.  Il peut utiliser un certificat valide publié par une autorité de certification.  
  
2.  Il peut choisir de signer le manifeste de déploiement avec un certificat auto\-signé.  L'inconvénient de cette approche est que l'application affiche "Éditeur Inconnu" lorsque l'utilisateur est invité à spécifier s'il faut l'installer.  Mais pour les petits clients, cela se traduit par un gain de temps et d'argent, car ils n'ont pas besoin d'acheter un certificat publié par une autorité de certification.  
  
3.  Enfin, le développeur peut inclure son propre certificat auto\-signé dans le package d'installation.  Mais des problèmes d'identité d'application peuvent survenir, comme indiqué plus haut dans cette rubrique.  
  
 L'inconvénient avec la méthode du projet de déploiement de l'installation est que la génération d'une application de déploiement personnalisée est longue et coûteuse.  
  
### Génération du manifeste de déploiement par le client  
 La troisième stratégie de déploiement consiste à ne confier au client que les fichiers et le manifeste d'application.  Dans ce scénario, le client doit utiliser le Kit de développement .NET Framework SDK pour générer et signer le manifeste de déploiement.  
  
 L'inconvénient de cette méthode est que le client doit installer les outils du Kit de développement .NET Framework SDK et qu'un développeur ou un administrateur système doit les maîtriser parfaitement.  Certains clients peuvent rechercher une solution qui requiert peu ou aucune connaissance technique de leur part.  
  
## Voir aussi  
 [Deploying ClickOnce Applications For Testing and Production Servers without Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)