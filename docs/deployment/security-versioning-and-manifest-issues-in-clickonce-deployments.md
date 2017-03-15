---
title: "Security, Versioning, and Manifest Issues in ClickOnce Deployments | Microsoft Docs"
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
  - "versioning, ClickOnce applications"
  - "ClickOnce applications, Windows Vista User Account Control"
  - "ClickOnce applications, versioning issues"
  - "security, ClickOnce applications"
  - "Windows 7, ClickOnce deployments"
  - "ClickOnce applications, manifest issues"
  - "User Account Control, ClickOnce applications"
  - "Windows Vista, ClickOnce deployments"
  - "manifests [ClickOnce]"
  - "ClickOnce applications, security issues"
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# Security, Versioning, and Manifest Issues in ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il existe divers problèmes concernant la sécurité de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], le contrôle de version de l'application, ainsi que la syntaxe et la sémantique de manifeste qui peuvent entraîner l'échec d'un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Contrôle de compte d'utilisateur ClickOnce et Windows Vista  
 Dans [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], les applications s'exécutent, par défaut, comme un utilisateur standard, même si l'utilisateur actuel se connecte avec un compte qui a des autorisations d'administrateur.  Si une application doit exécuter une action qui requiert des autorisations d'administrateur, elle en informe le système d'exploitation, qui invite alors l'utilisateur à saisir ses informations d'identification d'administrateur.  Cette fonctionnalité, appelée Contrôle de compte d'utilisateur, empêche les applications d'apporter des modifications pouvant affecter l'ensemble du système d'exploitation sans l'approbation explicite d'un utilisateur.  Les applications Windows déclarent qu'elles ont besoin de cette élévation d'autorisation en spécifiant l'attribut `requestedExecutionLevel` dans la section `trustInfo` de leur manifeste d'application.  
  
 Compte tenu du risque d'exposition des applications aux attaques d'élévation de sécurité, les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne peuvent pas demander d'élévation d'autorisation si le contrôle de compte d'utilisateur est activé pour le client.  Toute application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui essaie de définir son attribut `requestedExecutionLevel` à `requireAdministrator` ou `highestAvailable` ne s'installe pas sur [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  
  
 Dans certains cas, votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut essayer de s'exécuter avec des autorisations d'administrateur compte tenu de la logique de détection de programme d'installation logique sur [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  Dans ce cas, vous pouvez définir l'attribut `requestedExecutionLevel` dans le manifeste de l'application à `asInvoker`.  Cela entraînera l'exécution de l'application sans élévation. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] ajoute automatiquement cet attribut à tous les manifestes d'application.  
  
 Si vous développez une application qui requiert des autorisations d'administrateur pour la durée de vie entière de l'application, vous devez envisager le déploiement de l'application à l'aide de la technologie Windows Installer \(MSI\).  Pour plus d'informations, consultez [Principes fondamentaux de Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## Quotas pour l'application en ligne et applications de confiance partielle  
 Si votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] s'exécute en ligne et non via une installation, elle doit répondre au quota défini à part pour les applications en ligne.  De plus, une application de réseau qui s'exécute en confiance partielle, tel qu'avec un jeu restreint d'autorisations de sécurité, ne peut pas être supérieure à la moitié de la taille du quota.  
  
 Pour plus d'informations et d'instructions sur la manière de modifier le quota d'application en ligne, consultez [ClickOnce Cache Overview](../deployment/clickonce-cache-overview.md).  
  
## Problèmes de versioning  
 Vous pouvez rencontrer des problèmes si vous assignez des noms forts à votre assembly et que vous incrémentez le numéro de version d'assembly pour refléter une mise à jour de l'application.  Tout assembly compilé avec une référence à un assembly avec nom fort doit être recompilé, ou l'assembly tentera de référencer la version antérieure.  La raison en est que l'assembly utilise la valeur de la version ancienne dans sa demande de lien.  
  
 Par exemple, supposons que vous possédez un assembly avec nom fort dans son propre projet avec la version 1.0.0.0.  Après avoir compilé l'assembly, vous l'ajoutez en tant que référence au projet qui contient votre application principale.  Si vous mettez à jour l'assembly, que vous incrémentez la version à 1.0.0.1 et que vous essayez de le déployer sans recompiler également l'application, cette dernière ne réussira pas à charger l'assembly au moment de l'exécution.  
  
 Cette erreur peut se produire si vous modifiez manuellement les manifestes de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], mais elle ne doit pas se produire si vous générez votre déploiement avec [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## Spécification d'assemblys .NET Framework individuels dans le manifeste  
 Le chargement de votre application échouera si vous avez modifié manuellement un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour référencer une version antérieure d'un assembly [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Par exemple, si vous avez ajouté une référence à l'assembly System.Net pour une version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] antérieure à la version spécifiée dans le manifeste, une erreur se produit.  En général, vous ne devez pas essayer de spécifier des références aux assemblys [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] individuels, car la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sur laquelle votre application s'exécute est spécifiée comme une dépendance dans le manifeste d'application.  
  
## Problèmes d'analyse de manifestes  
 Les fichiers manifeste utilisés par [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont des fichiers XML qui doivent être correctement construits et valides : ils doivent respecter les règles de syntaxes XML et utiliser uniquement des éléments et des attributs définis dans le schéma XML pertinent.  
  
 La sélection, pour votre application, d'un nom contenant un caractère spécial, tel qu'un guillemet simple ou double, peut entraîner des problèmes dans un fichier manifeste.  Le nom de l'application fait partie de son identité [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Actuellement, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] n'analyse pas les identités qui contiennent des caractères spéciaux.  Si l'activation de votre application échoue, vérifiez que vous n'utilisez que des caractères alphabétiques et numériques pour le nom, et tentez à nouveau le déploiement.  
  
 Si vous avez modifié manuellement vos manifestes de déploiement ou d'application, vous les avez endommagés volontairement.  Un manifeste endommagé empêche une installation correcte de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Vous pouvez déboguer de telles erreurs au moment de l'exécution en cliquant sur **Détails** dans la boîte de dialogue **Erreur ClickOnce** et en lisant le message d'erreur dans le journal.  Le journal répertorie l'un des messages suivants :  
  
-   Description de l'erreur de syntaxe, numéro de ligne et position du caractère où l'erreur s'est produite.  
  
-   Nom d'un élément ou attribut utilisé, contraire au schéma du manifeste.  Si vous avez ajouté manuellement du code XML à vos manifestes, vous devez comparer le code ajouté aux schémas des manifestes.  Pour plus d'informations, consultez [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md) et [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
-   Conflit d'ID.  Les références de dépendance dans les manifestes d'application et du déploiement doivent être uniques au niveau des attributs `name` et `publicKeyToken`.  Si les deux attributs de deux éléments d'un manifeste correspondent, l'analyse du manifeste échoue.  
  
## Précautions lors de la modification manuelle de manifestes ou d'applications  
 Lorsque vous mettez à jour un manifeste d'application, vous devez signer à nouveau le manifeste de l'application et le manifeste de déploiement.  Le manifeste de déploiement contient une référence au manifeste de l'application qui inclut le hachage de ce fichier et sa signature numérique.  
  
### Précautions lors de l'utilisation du Fournisseur de déploiement  
 Le manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] comprend une propriété `deploymentProvider` qui désigne le chemin d'accès complet de l'emplacement dans lequel l'application doit être installée et gérée :  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Ce chemin d'accès est défini lorsque [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crée l'application et est obligatoire pour les applications installées.  Le chemin d'accès pointe sur l'emplacement standard à partir duquel le programme d'installation de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] doit installer l'application et rechercher les mises à jour.  Si vous utilisez la commande **xcopy** pour copier une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vers un emplacement différent, mais ne modifiez pas la propriété `deploymentProvider`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se réfère toujours à l'emplacement d'origine lorsqu'il tente de télécharger l'application.  
  
 Si vous souhaitez déplacer ou copier une application, vous devez également mettre à jour le chemin d'accès de `deploymentProvider` afin que le client installe réellement l'application à partir du nouvel emplacement.  La mise à jour de ce chemin d'accès pose un problème principalement si vous avez installé des applications.  Pour les applications en ligne qui sont toujours lancées par l'intermédiaire de l'URL d'origine, la définition du `deploymentProvider` est facultative.  Si la propriété `deploymentProvider` est définie, elle est respectée ; sinon, l'URL utilisée pour démarrer l'application est utilisée comme URL de base pour le téléchargement des fichiers d'application.  
  
> [!NOTE]
>  Chaque fois que vous mettez à jour le manifeste, vous devez également le signer à nouveau.  
  
## Voir aussi  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)