---
title: "Comment&#160;: installer un plug-in de contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation (Visual Studio SDK), les plug-ins de contrôle de code source"
  - "contrôle plug-ins de source, l’installation"
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Comment&#160;: installer un plug-in de contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Création d’un contrôle de code source du plug-in implique trois étapes :  
  
1.  Créer une DLL avec les fonctions définies dans la section de référence des API de plug-in de contrôle de Source de cette documentation.  
  
2.  Implémenter les fonctions définies par l’API de plug-in de contrôle de Source. Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelle, rendre les interfaces et les boîtes de dialogue disponibles à partir du plug-in.  
  
3.  Enregistrez la DLL en ajoutant des entrées de Registre appropriées.  
  
## <a name="integration-with-visual-studio"></a>Intégration à Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge la charge des plug-ins de contrôle de code source qui sont conformes à l’API de plug-in de contrôle de Source.  
  
### <a name="registering-the-source-control-plug-in"></a>L’inscription du plug-in de contrôle de code Source  
 Avant que le système de contrôle de code source peut appeler un environnement de développement intégré (IDE) en cours d’exécution, il doit d’abord localiser la source de DLL de plug-in qui exporte l’API de contrôle.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Pour inscrire la contrôle du code source DLL de plug-in  
  
1.  Ajoutez deux entrées sous la clé HKEY_LOCAL_MACHINE dans la sous-clé de LOGICIEL qui spécifie la sous-clé votre nom d’entreprise suivie de votre sous-clé de nom de produit. Le modèle est HKEY_LOCAL_MACHINE\SOFTWARE\\*[nom de société]*\\*[nom du produit]*\\*[Entrée]* = valeur. Les deux entrées sont toujours appelées SCCServerName et SCCServerPath. Chacun est une chaîne normale.  
  
     Par exemple, si le nom de votre société est Microsoft et votre produit de contrôle de code source nommé SourceSafe, ce chemin d’accès de Registre serait HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe. Dans cette sous-clé, la première entrée, SCCServerName, est une chaîne lisible par l’utilisateur de votre produit d’affectation de noms. La deuxième entrée, SCCServerPath, est le chemin d’accès complet à la source de contrôle DLL de plug-in qui doit se connecter l’IDE. Les éléments suivants fournissent des exemples d’entrées du Registre :  
  
    |Exemple d’entrée de Registre|Exemple de valeur|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  Le SCCServerPath est le chemin d’accès complet pour le plug-in SourceSafe. Votre plug-in de contrôle de code source utilise des noms de sociétés et de produits différents mais les mêmes chemins d’entrée de Registre.  
  
2.  Les entrées de Registre facultatives suivantes peuvent servir à modifier le comportement de votre plug-in de contrôle de code source. Ces entrées aller dans la même sous-clé SccServerName et SccServerPath.  
  
    -   L’entrée HideInVisualStudioregistry peut être utilisée si vous ne souhaitez pas que votre source de contrôle plug-in apparaissent dans la liste de sélection du plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cette entrée affecte également le basculement automatique pour le plug-in de contrôle de code source. Une utilisation possible pour cette entrée est si vous fournissez un package de contrôle de code source qui remplace votre plug-in de contrôle de code source, mais vous souhaitez faciliter l’utilisateur à migrer à partir de l’utilisation du plug-in pour le package de contrôle de source de contrôle de code source. Lorsque le package de contrôle de code source est installé, il définit cette entrée de Registre, ce qui masque le plug-in.  
  
         HideInVisualStudio est une valeur DWORD et est défini sur 1 pour masquer le plug-in ou 0 pour afficher le plug-in. Si l’entrée de Registre n’apparaît pas, le comportement par défaut est d’illustrer le plug-in.  
  
    -   L’entrée de Registre DisableSccManager peut être utilisée pour désactiver ou masquer la **lancer \< serveur de contrôle de code Source>** option de menu qui s’affiche sous le **fichier** -> **contrôle de code Source** sous-menu. En sélectionnant ce menu option appelle la [SccRunScc](../../extensibility/sccrunscc-function.md) (fonction). Votre plug-in de contrôle de code source, n’acceptent pas un programme externe et pouvez par conséquent que vous souhaitez désactiver ou masquer même le **lancer** option de menu.  
  
         DisableSccManager est une valeur DWORD est définie sur 0 pour permettre la **lancer \< serveur de contrôle de code Source>** option de menu, la valeur 1 pour désactiver l’option de menu et la valeur 2 pour masquer l’option de menu. Si cette entrée de Registre n’apparaît pas, le comportement par défaut est d’illustrer l’option de menu.  
  
    |Exemple d’entrée de Registre|Exemple de valeur|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Ajoutez la sous-clé SourceCodeControlProvider, sous la clé HKEY_LOCAL_MACHINE dans la sous-clé de LOGICIEL.  
  
     Sous cette sous-clé, l’entrée de Registre ProviderRegKey est définie à une chaîne qui représente la sous-clé que vous avez placées dans le Registre à l’étape 1. Le modèle est HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = LOGICIEL\\*[nom de société]*\\*[nom du produit]*.  
  
     Voici un exemple de contenu pour cette sous-clé.  
  
    |Entrée de Registre|Exemple de valeur|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Votre plug-in de contrôle de code source utilise la même sous-clé et noms d’entrée, mais la valeur sera différente.  
  
4.  Créez une sous-clé appelée InstalledSCCProviders sous la sous-clé SourceCodeControlProvider, puis placez une entrée sous cette sous-clé.  
  
     Le nom de cette entrée est le nom lisible par l’utilisateur du fournisseur (le même que la valeur spécifiée pour l’entrée SCCServerName) et la valeur est une fois encore, la sous-clé créée à l’étape 1. Le modèle est HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[nom d’affichage]* = LOGICIEL\\*[nom de société]*\\*[nom du produit]*.  
  
     Exemple :  
  
    |Exemple d’entrée de Registre|Exemple de valeur|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Il peut y avoir plusieurs source plug-ins de contrôle enregistrés de cette façon. Voici comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trouve tous installés plug-ins basés sur les API de plug-in de contrôle de Source de.  
  
## <a name="how-an-ide-locates-the-dll"></a>Comment un IDE recherche la DLL  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE a deux façons de trouver la source de contrôlent DLL de plug-in :  
  
-   Recherchez le contrôle de code source par défaut du plug-in et s’y connecter en mode silencieux.  
  
-   Rechercher source inscrit tous les plug-ins de contrôle, à partir de laquelle l’utilisateur choisit un.  
  
 Pour localiser la DLL dans la première méthode, l’IDE se présente sous la sous-clé HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider pour l’entrée ProviderRegKey. La valeur de cette entrée pointe vers une autre sous-clé. L’IDE recherche alors une entrée nommée SccServerPath dans ce deuxième sous-clé sous HKEY_LOCAL_MACHINE. La valeur de cette entrée pointe l’IDE à la DLL.  
  
> [!NOTE]
>  L’IDE ne charge pas la DLL à partir de chemins d’accès relatifs (par exemple,.\NewProvider.DLL). Un chemin d’accès complet à la DLL doit être spécifié (par exemple, c:\Providers\NewProvider.DLL). Cela renforce la sécurité de l’IDE en empêchant le chargement des DLL de plug-in non autorisés ou emprunt d’identité.  
  
 Pour localiser la DLL dans la seconde méthode, l’IDE se présente sous la sous-clé HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders pour toutes les entrées*.* Chaque entrée comporte un nom et une valeur. L’IDE affiche une liste de ces noms pour l’utilisateur*.* Lorsque l’utilisateur choisit un nom, l’IDE détecte que la valeur pour le nom qui pointe vers une sous-clé. L’environnement IDE recherche une entrée nommée SccServerPath dans cette sous-clé sous HKEY_LOCAL_MACHINE. La valeur de cette entrée pointe l’IDE à la DLL correcte.  
  
 Un plug-in de contrôle de code source doit prendre en charge les deux méthodes de recherche de la DLL et, par conséquent, définissez ProviderRegKey, en remplaçant le paramètre précédent. Plus important encore, il doit s’ajoute la liste des InstalledSccProviders pour l’utilisateur peut avoir un choix de quel plug-in de contrôle de code source à utiliser.  
  
> [!NOTE]
>  Étant donné que la clé HKEY_LOCAL_MACHINE est utilisée, les plug-in de contrôle qu’une seule source peut être enregistré comme le contrôle de code source par défaut du plug-in sur un ordinateur donné (Toutefois, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permet aux utilisateurs de déterminer quel plug-in de contrôle de code source qu’ils souhaitent utiliser réellement pour une solution spécifique). Au cours du processus d’installation, vérifiez si un plug-in de contrôle de code source est déjà défini ; Dans ce cas, demandez à l’utilisateur s’il faut définir le contrôle de source de plug-in en cours d’installation par défaut. Au cours de la désinstallation, ne supprimez pas d’autres sous-clés de Registre qui sont communes à tous les contrôle plug-ins de source dans HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider ; Supprimez uniquement votre sous-clé SCC.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Comment l’IDE détecte la prise en charge de la Version 1.2/1.3  
 Comment est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détecter si une fonctionnalité de version 1.2 et 1.3 de plug-in prend en charge l’API de plug-in de contrôle de code Source ? Pour déclarer une fonction avancée, le plug-in de contrôle de code source doit implémenter la fonction correspondante.  
  
 Tout d’abord, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vérifie la valeur retournée en appelant le [SccGetVersion](../../extensibility/sccgetversion-function.md). Elle doit être supérieure ou égale à la version 1.2.  
  
 Ensuite, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détermine si la nouvelle fonctionnalité particulier est pris en charge en examinant le `lpSccCaps` argument sur le [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Si les deux conditions suivantes sont remplies, les nouvelles fonctions prises en charge dans les versions 1.2 et 1.3 peuvent être appelées.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en route](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)