---
title: "Comment : installer un plug-in de contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab02b65e4a40f15da857038a45d9bcc2b88b1b83
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-a-source-control-plug-in"></a>Comment : installer un plug-in de contrôle de code Source
Création d’un contrôle de source de plug-in implique trois étapes :  
  
1.  Créer une DLL avec les fonctions définies dans la section de référence d’API de plug-in de contrôle de Source de cette documentation.  
  
2.  Implémenter les fonctions définies par l’API de plug-in de contrôle de Source. Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelle, rendre les interfaces et les boîtes de dialogue disponibles à partir du plug-in.  
  
3.  Inscrire la DLL en créant des entrées de Registre appropriées.  
  
## <a name="integration-with-visual-studio"></a>Intégration à Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge de la charge des plug-ins de contrôle de code source qui sont conformes à l’API de plug-in de contrôle de Source.  
  
### <a name="registering-the-source-control-plug-in"></a>L’inscription du plug-in de contrôle de code Source  
 Avant qu’un environnement de développement intégré (IDE) en cours d’exécution puisse appeler dans le système de contrôle de code source, il doit d’abord localiser la source de plug-in DLL qui exporte l’API de contrôle.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Pour inscrire la contrôle de code source DLL de plug-in  
  
1.  Ajoutez deux entrées sous la clé HKEY_LOCAL_MACHINE dans la sous-clé de logiciel qui spécifie votre sous-clé de nom de société suivi par le sous-clé de nom de produit. Le modèle est HKEY_LOCAL_MACHINE\SOFTWARE\\*[nom de société]*\\*[nom du produit]*\\*[Entrée]* = valeur. Les deux entrées sont toujours appelées SCCServerName et SCCServerPath. Chacun est une chaîne normale.  
  
     Par exemple, si le nom de votre société est Microsoft et votre produit de contrôle de code source nommé SourceSafe, ce chemin d’accès du Registre serait HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe. Dans cette sous-clé, la première entrée, SCCServerName, est une chaîne lisible par l’utilisateur de votre produit d’affectation de noms. La deuxième entrée, SCCServerPath, est le chemin d’accès complet à la source de contrôle DLL plug-in qui doit se connecter l’IDE. La section suivante fournit des exemples d’entrées du Registre :  
  
    |Exemple d’entrée de Registre|Exemple de valeur|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  Le SCCServerPath est le chemin d’accès complet pour le plug-in SourceSafe. Votre plug-in de contrôle de code source utilise des noms de sociétés et de produits différents mais les mêmes chemins d’entrée de Registre.  
  
2.  Les entrées de Registre facultative suivante peuvent être utilisées pour modifier le comportement de votre plug-in de contrôle de code source. Ces entrées aller dans la même sous-clé SccServerName et SccServerPath.  
  
    -   L’entrée HideInVisualStudioregistry peut être utilisée si vous ne souhaitez pas que votre source de contrôle plug-in s’affichent dans la liste de sélection du plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cette entrée affectent également le basculement automatique pour le plug-in de contrôle de code source. Une utilisation possible de cette entrée est si vous fournissez un package de contrôle de code source qui remplace votre plug-in de contrôle de code source, mais que vous souhaitez faciliter l’utilisation de l’utilisateur à migrer à partir de l’utilisation du contrôle de source du plug-in pour le package de contrôle de code source. Lorsque le package de contrôle de code source est installé, il définit cette entrée de Registre, qui masque le plug-in.  
  
         HideInVisualStudio est une valeur DWORD et est définie sur 1 pour masquer le plug-in ou 0 pour afficher le plug-in. Si l’entrée de Registre n’apparaît pas, le comportement par défaut est d’illustrer le plug-in.  
  
    -   L’entrée de Registre DisableSccManager peut être utilisée pour désactiver ou masquer la **lancer \<Source Control Server >** option de menu qui s’affiche sous le **fichier**  ->   **Contrôle de code source** sous-menu. Sélection de ce menu option appelle la [SccRunScc](../../extensibility/sccrunscc-function.md) (fonction). Votre plug-in de contrôle de code source, n’acceptent pas un programme externe et pouvez par conséquent que vous souhaitez désactiver ou masquer même le **lancer** option de menu.  
  
         DisableSccManager est une valeur DWORD est définie sur 0 pour activer la **lancer \<Source Control Server >** option de menu, la valeur 1 pour désactiver l’option de menu et la valeur 2 pour masquer l’option de menu. Si cette entrée de Registre n’apparaît pas, le comportement par défaut est d’illustrer l’option de menu.  
  
    |Exemple d’entrée de Registre|Exemple de valeur|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Ajoutez la sous-clé SourceCodeControlProvider, sous la clé HKEY_LOCAL_MACHINE dans la sous-clé de logiciel.  
  
     Sous cette sous-clé, l’entrée de Registre ProviderRegKey est définie à une chaîne qui représente la sous-clé que vous avez placées dans le Registre à l’étape 1. Le modèle est HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = logiciel\\*[nom de société]*\\*[nom du produit]*.  
  
     Voici un exemple de contenu pour cette sous-clé.  
  
    |Entrée de Registre|Exemple de valeur|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Votre plug-in de contrôle de code source utilisera le sous-clé même et les noms d’entrée, mais la valeur sera différente.  
  
4.  Créez une sous-clé appelée InstalledSCCProviders sous la sous-clé SourceCodeControlProvider, puis placez une entrée sous cette sous-clé.  
  
     Le nom de cette entrée est le nom lisible par l’utilisateur du fournisseur (le même que la valeur spécifiée pour l’entrée SCCServerName) et la valeur est, une fois encore, la sous-clé créée à l’étape 1. Le modèle est HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[nom d’affichage]* = logiciel\\*[nom de société]* \\ *[nom du produit]*.  
  
     Exemple :  
  
    |Exemple d’entrée de Registre|Exemple de valeur|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Il peut y avoir plusieurs source plug-ins de contrôle enregistrés de cette façon. Voici comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trouve tous installés plug-ins basée sur les API de plug-in de contrôle de Source.  
  
## <a name="how-an-ide-locates-the-dll"></a>Comment un IDE recherche la DLL  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE a deux façons de trouver la source de contrôlent les DLL de plug-in :  
  
-   Rechercher le contrôle de code source par défaut du plug-in et s’y connecter en mode silencieux.  
  
-   Trouver source enregistré tous les plug-ins de contrôle, à partir de laquelle l’utilisateur choisit une.  
  
 Pour trouver la DLL dans la première méthode, l’IDE se présente sous la sous-clé HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider pour l’entrée ProviderRegKey. La valeur de cette entrée pointe vers une autre sous-clé. L’IDE recherche alors une entrée nommée SccServerPath dans ce deuxième sous-clé sous HKEY_LOCAL_MACHINE. La valeur de cette entrée pointe l’IDE à la DLL.  
  
> [!NOTE]
>  L’IDE ne charge pas la DLL à partir de chemins d’accès relatifs (par exemple,.\NewProvider.DLL). Un chemin d’accès complet à la DLL doit être spécifié (par exemple, c:\Providers\NewProvider.DLL). Cela renforce la sécurité de l’IDE en empêchant le chargement de DLL de plug-in non autorisés ou avec emprunt d’identité.  
  
 Pour trouver la DLL dans la deuxième méthode, l’IDE se présente sous la sous-clé HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders pour toutes les entrées*.* Chaque entrée a un nom et une valeur. L’IDE affiche une liste de ces noms à l’utilisateur*.* Lorsque l’utilisateur choisit un nom, l’IDE détecte que la valeur pour le nom sélectionné qui pointe vers une sous-clé. L’environnement IDE recherche une entrée nommée SccServerPath dans cette sous-clé sous HKEY_LOCAL_MACHINE. La valeur de cette entrée pointe l’IDE à la DLL correcte.  
  
 Un plug-in de contrôle de code source doit prendre en charge les deux façons de trouver la DLL et, par conséquent, définissez ProviderRegKey, en remplaçant le paramètre précédent. Plus important encore, il doit lui-même ajouter à la liste des InstalledSccProviders afin de l’utilisateur peut avoir un choix de quel plug-in de contrôle de code source à utiliser.  
  
> [!NOTE]
>  Étant donné que la clé HKEY_LOCAL_MACHINE est utilisée, le plug-in de contrôle qu’une seule source peut être enregistré comme le contrôle de code source par défaut du plug-in sur un ordinateur donné (Toutefois, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permet aux utilisateurs de déterminer quel plug-in de contrôle de code source qu’ils souhaitent utiliser réellement pour un solution spécifique). Au cours du processus d’installation, vérifiez si un plug-in de contrôle de code source est déjà défini ; Dans ce cas, demandez à l’utilisateur définir le nouveau contrôle de code source en cours d’installation par défaut du plug-in ou non. Au cours de la désinstallation, ne supprimez pas d’autres sous-clés de Registre qui sont communes à tous les source plug-ins de contrôle dans HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider ; supprimer uniquement le sous-clé SCC.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>La manière dont l’IDE détecte la prise en charge de la Version 1.2/1.3  
 Comment est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détecter si une fonctionnalité de version 1.2 et 1.3 de plug-in prend en charge l’API de plug-in de contrôle de code Source ? Pour déclarer des fonctionnalités avancées, le plug-in de contrôle de code source doit implémenter la fonction correspondante.  
  
 Tout d’abord, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vérifie la valeur retournée en appelant le [SccGetVersion](../../extensibility/sccgetversion-function.md). Il doit être supérieure ou égale à 1.2.  
  
 Ensuite, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détermine si la nouvelle fonctionnalité particulier est pris en charge en examinant le `lpSccCaps` argument sur le [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Si ces deux conditions sont remplies, les nouvelles fonctions prises en charge dans les versions 1.2 et 1.3 peuvent être appelées.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)