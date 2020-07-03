---
title: 'Comment : installer un plug-in de contrôle de code source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f88e4781115fa7a5fac54826304ab32472eeefb
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905356"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Comment : installer un plug-in de contrôle de code source
La création d’un plug-in de contrôle de code source implique trois étapes :

1. Créez une DLL avec les fonctions définies dans la section Référence de l’API du plug-in de contrôle de code source de cette documentation.

2. Implémentez les fonctions définies par l’API du plug-in de contrôle de code source. Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelle pour celui-ci, rendez les interfaces et les boîtes de dialogue disponibles à partir du plug-in.

3. Enregistrez la DLL en créant les entrées de Registre appropriées.

## <a name="integration-with-visual-studio"></a>Intégration à Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge les plug-ins de contrôle de code source conformes à l’API de plug-in de contrôle de code source.

### <a name="register-the-source-control-plug-in"></a>Inscrire le plug-in de contrôle de code source
 Avant qu’un environnement de développement intégré (IDE) en cours d’exécution puisse appeler le système de contrôle de code source, il doit d’abord rechercher la DLL du plug-in de contrôle de code source qui exporte l’API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Pour inscrire la DLL du plug-in de contrôle de code source

1. Ajoutez deux entrées sous la clé **HKEY_LOCAL_MACHINE** dans la sous-clé **Software** qui spécifie la sous-clé de nom de votre société, suivie de la sous-clé de nom de produit. Le modèle est **HKEY_LOCAL_MACHINE \\ \<company name> \\ \<product name> \\ \<entry> **  =  *valeur*\Software. Les deux entrées sont toujours appelées **SCCServerName** et **SCCServerPath**. Chaque est une chaîne normale.

    Par exemple, si le nom de votre société est Microsoft et que votre produit de contrôle de code source est nommé SourceSafe, ce chemin de Registre serait **HKEY_LOCAL_MACHINE \software\microsoft\sourcesafe**. Dans cette sous-clé, la première entrée, **SCCServerName**, est une chaîne lisible par l’utilisateur qui nomme votre produit. La deuxième entrée, **SCCServerPath**, est le chemin d’accès complet à la dll du plug-in de contrôle de code source à laquelle l’IDE doit se connecter. Vous trouverez ci-dessous des exemples d’entrées de Registre :

   |Exemple d’entrée de Registre|Exemple de valeur|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath est le chemin d’accès complet au plug-in SourceSafe. Votre plug-in de contrôle de code source utilise des noms de sociétés et de produits différents, mais les mêmes chemins d’accès d’entrée de registre.

2. Les entrées de Registre facultatives suivantes peuvent être utilisées pour modifier le comportement de votre plug-in de contrôle de code source. Ces entrées sont placées dans la même sous-clé que **SccServerName** et **SccServerPath**.

   - L’entrée **HideInVisualStudioregistry** peut être utilisée si vous ne souhaitez pas que le plug-in de contrôle de code source apparaisse dans la liste de **sélection de plug-** in de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Cette entrée affecte également le basculement automatique vers le plug-in de contrôle de code source. Une utilisation possible de cette entrée est si vous fournissez un package de contrôle de code source qui remplace votre plug-in de contrôle de code source, mais que vous souhaitez faciliter la migration de l’utilisateur à l’aide du plug-in de contrôle de code source vers le package de contrôle de code source. Lorsque le package de contrôle de code source est installé, il définit cette entrée de Registre, qui masque le plug-in.

      **HideInVisualStudio** est une valeur DWORD et est définie sur *1* pour masquer le plug-in ou sur *0* pour afficher le plug-in. Si l’entrée de Registre n’apparaît pas, le comportement par défaut consiste à afficher le plug-in.

   - L’entrée de Registre **DisableSccManager** peut être utilisée pour désactiver ou masquer l’option de menu de ** \<Source Control Server> lancement** qui apparaît normalement dans le sous **File**  >  -menu**contrôle de source** de fichier. La sélection de cette option de menu appelle la fonction [SccRunScc](../../extensibility/sccrunscc-function.md) . Votre plug-in de contrôle de code source ne prend peut-être pas en charge un programme externe. par conséquent, vous souhaiterez peut-être désactiver ou même masquer l’option de menu **lancer** .

      **DisableSccManager** est une valeur DWORD qui est définie sur *0* pour activer l’option de menu **Launch \<Source Control Server> ** , à la valeur *1* pour désactiver l’option de menu et à la valeur *2* pour masquer l’option de menu. Si cette entrée de Registre n’apparaît pas, le comportement par défaut consiste à afficher l’option de menu.

   | Exemple d’entrée de Registre | Exemple de valeur |
   | - |--------------|
   | HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Ajoutez la sous-clé, **SourceCodeControlProvider**, sous la clé **HKEY_LOCAL_MACHINE** dans la sous-clé **Software** .

    Sous cette sous-clé, l’entrée de Registre **ProviderRegKey** est définie sur une chaîne qui représente la sous-clé que vous avez placée dans le registre à l’étape 1. Le modèle est **HKEY_LOCAL_MACHINE**  =  *logiciel \software\sourcecodecontrolprovider\providerregkey \\<nom de la société \> \\<\> nom du produit*.

    Voici un exemple de contenu pour cette sous-clé.

   |Entrée de Registre|Exemple de valeur|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE \SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Votre plug-in de contrôle de code source utilisera les mêmes noms de sous-clés et d’entrées, mais la valeur sera différente.

4. Créez une sous-clé nommée **InstalledSCCProviders** sous la sous-clé **SourceCodeControlProvider** , puis placez une entrée sous cette sous-clé.

    Le nom de cette entrée est le nom lisible par l’utilisateur du fournisseur (identique à la valeur spécifiée pour l’entrée SCCServerName), et la valeur est, une fois encore, la sous-clé créée à l’étape 1. Le modèle est **HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider\installedsccproviders \\<nom complet \> **du logiciel<nom de la  =  * \\ société \> \\<nom \> du produit*.

    Par exemple :

   |Exemple d’entrée de Registre|Exemple de valeur|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE Visual SourceSafe \SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Plusieurs plug-ins de contrôle de code source peuvent être inscrits de cette façon. Voici comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recherche tous les plug-ins basés sur des API de plug-in de contrôle de code source installés.

## <a name="how-an-ide-locates-the-dll"></a>Comment un IDE localise la DLL
 L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE a deux façons de rechercher la dll du plug-in de contrôle de code source :

- Recherchez le plug-in de contrôle de code source par défaut et connectez-vous à ce dernier en mode silencieux.

- Recherche tous les plug-ins de contrôle de code source inscrits, à partir desquels l’utilisateur en choisit un.

  Pour localiser la DLL de la première manière, l’IDE recherche l’entrée **ProviderRegKey**dans la sous-clé **HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider** . La valeur de cette entrée pointe vers une autre sous-clé. L’IDE recherche ensuite une entrée nommée **SccServerPath** dans cette deuxième sous-clé sous **HKEY_LOCAL_MACHINE**. La valeur de cette entrée pointe l’IDE vers la DLL.

> [!NOTE]
> L’IDE ne charge pas les dll à partir de chemins d’accès relatifs (par exemple, *.\NewProvider.DLL*). Un chemin d’accès complet à la DLL doit être spécifié (par exemple, *c:\Providers\NewProvider.DLL*). Cela renforce la sécurité de l’environnement de développement intégré (IDE) en empêchant le chargement de dll de plug-in non autorisées ou empruntées.

 Pour localiser la DLL de la seconde manière, l’IDE recherche toutes les entrées sous la sous-clé **HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider\installedsccproviders** . Chaque entrée a un nom et une valeur. L’IDE affiche une liste de ces noms pour l’utilisateur. Lorsque l’utilisateur choisit un nom, l’IDE recherche la valeur du nom sélectionné qui pointe vers une sous-clé. L’IDE recherche une entrée nommée **SccServerPath** dans cette sous-clé sous **HKEY_LOCAL_MACHINE**. La valeur de cette entrée pointe l’IDE vers la DLL correcte.

 Un plug-in de contrôle de code source doit prendre en charge les deux méthodes de recherche de la DLL et, par conséquent, définit **ProviderRegKey**, en remplaçant les paramètres précédents. Plus important encore, il doit s’ajouter à la liste des **InstalledSccProviders** pour que l’utilisateur puisse choisir le plug-in de contrôle de code source à utiliser.

> [!NOTE]
> Étant donné que la clé de **HKEY_LOCAL_MACHINE** est utilisée, un seul plug-in de contrôle de code source peut être enregistré en tant que plug-in de contrôle de code source par défaut sur un ordinateur donné (Toutefois, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permet aux utilisateurs de déterminer le plug-in de contrôle de code source qu’ils souhaitent réellement utiliser pour une solution particulière). Pendant votre processus d’installation, vérifiez si un plug-in de contrôle de code source est déjà défini. dans ce cas, demandez à l’utilisateur s’il faut ou non définir le nouveau plug-in de contrôle de code source en cours d’installation par défaut. Pendant la désinstallation, ne supprimez pas les autres sous-clés de Registre qui sont communes à tous les plug-ins de contrôle de code source dans **HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider**; Supprimez uniquement votre sous-clé SCC particulière.

## <a name="how-the-ide-detects-version-1213-support"></a>Comment l’IDE détecte la prise en charge de la version 1.2/1.3
 Comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détecter si un plug-in prend en charge les fonctionnalités de l’API de plug-in de contrôle de code source version 1,2 et 1,3 ? Pour déclarer une fonctionnalité avancée, le plug-in de contrôle de code source doit implémenter la fonction correspondante :

 Tout d’abord, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vérifie la valeur retournée en appelant [SccGetVersion](../../extensibility/sccgetversion-function.md). Elle doit être supérieure ou égale à 1,2.

 Détermine ensuite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si la nouvelle fonctionnalité particulière est prise en charge en examinant l' `lpSccCaps` argument sur le [SccInitialize](../../extensibility/sccinitialize-function.md).

 Si ces deux conditions sont remplies, les nouvelles fonctions prises en charge dans les versions 1,2 et 1,3 peuvent être appelées.

## <a name="see-also"></a>Voir aussi
- [Prise en main des plug-ins de contrôle de code source](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
