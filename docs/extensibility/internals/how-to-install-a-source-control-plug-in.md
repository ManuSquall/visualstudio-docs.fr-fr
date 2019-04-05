---
title: 'Procédure : Installer un plug-in de contrôle de code Source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46e93b07ddf65d50ebf92f04eda14e93fbfeba74
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58323384"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Procédure : Installer un plug-in de contrôle de code source
Création d’un contrôle de source de plug-in implique trois étapes :

1. Créer une DLL avec les fonctions définies dans la section de référence d’API de plug-in de contrôle de Source de cette documentation.

2. Implémentez les fonctions définies par l’API de plug-in de contrôle de Source. Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appels, proposer les interfaces et les boîtes de dialogue du plug-in.

3. Inscrivez la DLL en créant des entrées de Registre appropriées.

## <a name="integration-with-visual-studio"></a>Intégration à Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge de la charge des plug-ins de contrôle de source qui sont conformes à l’API de plug-in de contrôle de Source.

### <a name="register-the-source-control-plug-in"></a>Inscrire le plug-in de contrôle de code source
 Avant qu’un environnement de développement intégré (IDE) en cours d’exécution puisse appeler dans le système de contrôle source, il doit tout d’abord rechercher la source de contrôler les DLL de plug-in qui exporte l’API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Pour inscrire la source de contrôler les DLL de plug-in

1. Ajout de deux entrées sous la **HKEY_LOCAL_MACHINE** clé dans le **logiciel** sous-clé qui spécifie la sous-clé de votre nom d’entreprise suivie de votre sous-clé de nom de produit. Le modèle est **HKEY_LOCAL_MACHINE\SOFTWARE\\\<nom de la société >\\\<nom du produit >\\\<entrée >**  =  *valeur*. Les deux entrées sont toujours appelées **SCCServerName** et **SCCServerPath**. Chacun est une chaîne normale.

    Par exemple, si le nom de votre entreprise est Microsoft et votre produit de contrôle de code source est nommé SourceSafe, ce chemin d’accès de Registre serait **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. Dans cette sous-clé, la première entrée, **SCCServerName**, est une chaîne lisible par l’utilisateur de votre produit d’affectation de noms. La deuxième entrée, **SCCServerPath**, est le chemin d’accès complet à la source de contrôler les DLL de plug-in qui l’IDE doit se connecter. Vous trouverez ci-dessous des exemples d’entrées du Registre :

   |Exemple d’entrée de Registre|Exemple de valeur|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   >  SCCServerPath est le chemin d’accès complet pour le plug-in SourceSafe. Votre plug-in de contrôle de code source utilise des noms de société et le produit différents mais les mêmes chemins d’entrée de Registre.

2. Les entrées de Registre facultative suivante peuvent être utilisées pour modifier le comportement de votre plug-in de contrôle de code source. Ces entrées accédez dans la même sous-clé comme **SccServerName** et **SccServerPath**.

   - Le **HideInVisualStudioregistry** entrée peut être utilisée si vous ne souhaitez pas votre source de contrôle-plug-in apparaissent dans le **sélection du plug-in** liste de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cette entrée affecte également le basculement automatique pour le plug-in de contrôle de code source. Une utilisation possible de cette entrée est si vous fournissez un package de contrôle de code source qui remplace votre plug-in de contrôle de code source, mais que vous souhaitez faciliter l’utilisateur à migrer à partir de l’utilisation du contrôle de source plug-in pour le package de contrôle de code source. Lorsque le package de contrôle de code source est installé, il définit cette entrée de Registre, qui masque le plug-in.

      **HideInVisualStudio** est une valeur DWORD et est défini sur *1* pour masquer le plug-in ou *0* pour afficher le plug-in. Si l’entrée de Registre n’apparaît pas, le comportement par défaut consiste à afficher le plug-in.

   - Le **DisableSccManager** entrée de Registre peut être utilisée pour désactiver ou masquer la **lancer \<Source Control Server >** option de menu qui s’affiche normalement sous le **fichier**  >  **Contrôle de code source** sous-menu. En sélectionnant ce menu option appelle le [SccRunScc](../../extensibility/sccrunscc-function.md) (fonction). Votre plug-in de contrôle de code source, n’acceptent pas un programme externe et pourrez donc que vous souhaitez désactiver ou masquer même le **lancer** option de menu.

      **DisableSccManager** est une valeur DWORD et est défini sur *0* pour activer la **lancer \<Source Control Server >** option de menu, la valeur *1* à désactiver l’option de menu et la valeur *2* pour masquer l’option de menu. Si cette entrée de Registre n’apparaît pas, le comportement par défaut consiste à afficher l’option de menu.

   | Exemple d’entrée de Registre | Exemple de valeur |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |


3. Ajouter la sous-clé, **SourceCodeControlProvider**, sous le **HKEY_LOCAL_MACHINE** clé dans le **logiciel** sous-clé.

    Sous cette sous-clé, l’entrée de Registre **ProviderRegKey** est définie sur une chaîne qui représente la sous-clé que vous avez placées dans le Registre à l’étape 1. Le modèle est **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *logiciel\\< nom de la société\>\\< nom du produit \>*.

    Voici un exemple de contenu pour cette sous-clé.

   |Entrée de Registre|Exemple de valeur|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   >  Votre plug-in de contrôle de code source utilise la même sous-clé et les noms d’entrée, mais la valeur sera différente.

4. Créez une sous-clé nommée **InstalledSCCProviders** sous le **SourceCodeControlProvider** sous-clé, puis placez une entrée sous cette sous-clé.

    Le nom de cette entrée est le nom lisible par l’utilisateur du fournisseur (le même que la valeur spécifiée pour l’entrée SCCServerName), et la valeur est, une fois encore, la sous-clé créée à l’étape 1. Le modèle est **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\< nom d’affichage\>** = *logiciel\\< entreprise nom\>\\< nom du produit\>*.

    Exemple :

   |Exemple d’entrée de Registre|Exemple de valeur|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   >  Il peut y avoir plusieurs source plug-ins de contrôle enregistrés de cette façon. Voici comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tous installés plug-ins basée sur les API de plug-in de contrôle de Source de recherche.

## <a name="how-an-ide-locates-the-dll"></a>Comment un IDE localise la DLL
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE dispose de deux façons de trouver la source de contrôlent les DLL de plug-in :

- Plug-in de trouver le contrôle de code source par défaut et s’y connecter en mode silencieux.

- Trouver source inscrite tous les plug-ins de contrôle, à partir de laquelle l’utilisateur choisit une.

  Pour trouver la DLL dans la première méthode, l’IDE se présente sous la **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** sous-clé pour l’entrée **ProviderRegKey**. La valeur de cette entrée pointe vers une autre sous-clé. L’interface IDE recherche ensuite une entrée nommée **SccServerPath** dans ce deuxième sous-clé sous **HKEY_LOCAL_MACHINE**. La valeur de cette entrée pointe l’IDE à la DLL.

> [!NOTE]
>  L’IDE ne charge pas les DLL à partir de chemins d’accès relatifs (par exemple, *.\NewProvider.DLL*). Un chemin d’accès complet à la DLL doit être spécifié (par exemple, *c:\Providers\NewProvider.DLL*). Cela renforce la sécurité de l’IDE en empêchant le chargement des DLL de plug-in non autorisés ou avec emprunt d’identité.

 Pour trouver la DLL dans la deuxième méthode, l’IDE se présente sous la **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** sous-clé pour toutes les entrées. Chaque entrée comporte un nom et une valeur. L’IDE affiche une liste de ces noms à l’utilisateur. Lorsque l’utilisateur choisit un nom, l’IDE détecte que la valeur pour le nom sélectionné qui pointe vers une sous-clé. L’interface IDE recherche une entrée nommée **SccServerPath** dans cette sous-clé sous **HKEY_LOCAL_MACHINE**. La valeur de cette entrée pointe l’IDE à la DLL correcte.

 Un plug-in de contrôle de code source doit prendre en charge les deux façons de trouver la DLL et, par conséquent, définit **ProviderRegKey**, en remplaçant tout paramètre antérieur. Plus important encore, il doit s’ajouter à la liste des **InstalledSccProviders** afin de l’utilisateur peut avoir le choix entre le plug-in de contrôle de code source à utiliser.

> [!NOTE]
>  Étant donné que le **HKEY_LOCAL_MACHINE** clé est utilisée, le plug-in de contrôle qu’une seule source peut être inscrit en tant que le contrôle de code source par défaut plug-in sur un ordinateur donné (Toutefois, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permet aux utilisateurs de déterminer quel plug-in de contrôle de code source ils souhaitent utiliser réellement pour une solution spécifique). Pendant votre processus d’installation, vérifiez si un plug-in de contrôle de code source est déjà défini ; Dans ce cas, demandez à l’utilisateur s’il faut définir le contrôle de code source nouveau plug-in en cours d’installation par défaut. Lors de la désinstallation, ne supprimez pas d’autres sous-clés de Registre qui sont communes à toutes les sources plug-ins de contrôle dans **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; supprimer uniquement votre sous-clé SCC particulier.

## <a name="how-the-ide-detects-version-1213-support"></a>Comment l’IDE détecte la prise en charge de la version 1.2/1.3
 Comment est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détecter si une fonctionnalité de version 1.2 et 1.3 de plug-in prend en charge l’API de plug-in de contrôle de code Source ? Pour déclarer la fonctionnalité avancée, le plug-in de contrôle de code source doit implémenter la fonction correspondante :

 Tout d’abord, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vérifie la valeur retournée en appelant le [SccGetVersion](../../extensibility/sccgetversion-function.md). Il doit être supérieure ou égale à la version 1.2.

 Ensuite, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détermine si la nouvelle fonctionnalité particulier est pris en charge en examinant le `lpSccCaps` argument sur le [SccInitialize](../../extensibility/sccinitialize-function.md).

 Si les deux conditions suivantes sont remplies, les nouvelles fonctions prises en charge dans les versions 1.2 et 1.3 peuvent être appelées.

## <a name="see-also"></a>Voir aussi
- [Bien démarrer avec les plug-ins de contrôle de code source](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)