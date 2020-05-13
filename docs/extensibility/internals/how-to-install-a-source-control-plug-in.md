---
title: 'Comment : Installer un plug-in de contrôle des sources Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707996"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Comment : Installer un plug-in de contrôle source
La création d’un plug-in de contrôle des sources comporte trois étapes :

1. Créez un DLL avec les fonctions définies dans la section de référence de cette documentation.

2. Implémenter les fonctions définies par l’API de contrôle source. Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vous l’exigez, rendre les interfaces et les boîtes de dialogue disponibles à partir du plug-in.

3. Enregistrez le DLL en faisant les entrées appropriées de registre.

## <a name="integration-with-visual-studio"></a>Intégration à Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge les plug-ins de contrôle des sources qui se conforment à l’API de contrôle source.

### <a name="register-the-source-control-plug-in"></a>Enregistrez le plug-in de contrôle source
 Avant qu’un environnement de développement intégré en cours d’exécution (IDE) puisse faire appel au système de contrôle source, il doit d’abord trouver le DLL de contrôle source qui exporte l’API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Pour enregistrer le plug-in de contrôle source DLL

1. Ajoutez deux entrées sous la clé **HKEY_LOCAL_MACHINE** dans le sous-clé **SOFTWARE** qui spécifie votre sous-clé de nom d’entreprise suivie de votre sous-clé de nom de produit. Le modèle est **HKEY_LOCAL_MACHINE-LOGICIEL\\\<nom de \\ \<l’entreprise>\\ \<nom de produit>entrée>**  =  *valeur*. Les deux entrées sont toujours appelées **SCCServerName** et **SCCServerPath**. Chacun est une chaîne régulière.

    Par exemple, si votre nom d’entreprise est Microsoft et que votre produit de contrôle source s’appelle SourceSafe, alors cette trajectoire de registre serait **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe**. Dans ce sous-clé, la première entrée, **SCCServerName**, est une chaîne lisible à l’utilisateur nommant votre produit. La deuxième entrée, **SCCServerPath**, est le chemin complet vers le contrôle source plug-in DLL que l’IDE devrait se connecter à. Ce qui suit fournit des exemples d’inscriptions au registre :

   |Entrée du registre des échantillons|Exemple de valeur|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe-SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe-SCCServerPath|*c: vss-win32-ssscc.dll*|

   > [!NOTE]
   > SCCServerPath est le chemin complet vers le plug-in SourceSafe. Votre plug-in de contrôle source utilisera différents noms d’entreprise et de produit, mais les mêmes voies d’entrée de registre.

2. Les entrées de registre facultative suivantes peuvent être utilisées pour modifier le comportement de votre plug-in de contrôle source. Ces entrées vont dans le même sous-clé que **SccServerName** et **SccServerPath**.

   - **L’entrée HideInVisualStudioregistry** peut être utilisée si vous ne voulez pas que votre contrôle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]source-plug-in d’apparaître dans la liste **plug-in Sélection** de . Cette entrée affectera également le passage automatique au plug-in de contrôle source. Une utilisation possible pour cette entrée est si vous fournissez un paquet de contrôle source qui remplace votre plug-in de contrôle source, mais vous voulez le rendre plus facile pour l’utilisateur de migrer de l’utilisation du plug-in de contrôle source au paquet de contrôle source. Lorsque le paquet de contrôle source est installé, il définit cette entrée de registre, qui cache le plug-in.

      **HideInVisualStudio** est une valeur DWORD et est réglé à *1* pour cacher le plug-in ou *0* pour montrer le plug-in. Si l’entrée du registre n’apparaît pas, le comportement par défaut est d’afficher le plug-in.

   - L’entrée de registre **DisableSccManager** peut être utilisée pour désactiver ou masquer le **serveur de contrôle source de lancement \<>** option de menu qui apparaît normalement sous le sous-marin de contrôle de**source** **de fichiers.** >  La sélection de cette option de menu appelle la fonction [SccRunScc.](../../extensibility/sccrunscc-function.md) Votre plug-in de contrôle source peut ne pas prendre en charge un programme externe et donc vous pouvez désactiver ou même cacher l’option de menu **de lancement.**

      **DisableSccManager** est une valeur DWORD et est réglé à *0* pour activer le **serveur de contrôle source de lancement \<>** option de menu, réglé à *1* pour désactiver l’option de menu, et réglé à *2* pour masquer l’option de menu. Si cette entrée de registre n’apparaît pas, le comportement par défaut est de montrer l’option de menu.

   | Entrée de registre d’échantillon | Exemple de valeur |
   | - |--------------|
   | HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe-HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe-DisableSccManager | 1 |

3. Ajouter le sous-clé, **SourceCodeControlProvider**, sous la **clé HKEY_LOCAL_MACHINE** dans le sous-clé **SOFTWARE.**

    En vertu de cette sous-clé, l’entrée de registre **ProviderRegKey** est configuré à une chaîne qui représente la sous-clé que vous avez placé dans le registre à l’étape 1. Le modèle est **HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider-ProviderRegKey** = *SOFTWARE\\<nom\> \\ de l’entreprise<nom\>de produit*.

    Ce qui suit est le contenu de l’échantillon pour ce sous-clé.

   |Entrée de Registre|Exemple de valeur|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider-ProviderRegKey|SOFTWARE-Microsoft-SourceSafe|

   > [!NOTE]
   > Votre plug-in de contrôle source utilisera les mêmes sous-noms et les noms d’entrée, mais la valeur sera différente.

4. Créez un sous-clé nommé **InstalledSCCProviders** sous la sous-clé **SourceCodeControlProvider,** puis placez une entrée sous ce sous-clé.

    Le nom de cette entrée est le nom lisible par l’utilisateur du fournisseur (la même valeur que la valeur spécifiée pour l’entrée SCCServerName), et la valeur est, une fois de plus, le sous-clé créé à l’étape 1. Le modèle est **\\ HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider-InstalledSCCProviders<\>nom** = d’affichage SOFTWARE*\\ \> \\<nom de\>l’entreprise<nom de produit*.

    Par exemple :

   |Entrée de registre d’échantillon|Exemple de valeur|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider-InstalledSCCProviders-Microsoft SourceSafe visual|SOFTWARE-Microsoft-SourceSafe|

   > [!NOTE]
   > Il peut y avoir plusieurs plug-ins de contrôle de source enregistrés de cette façon. C’est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ainsi que trouve tous les plug-ins à base d’API de contrôle de source installés.

## <a name="how-an-ide-locates-the-dll"></a>Comment un IDE localise le DLL
 L’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a deux façons de trouver le contrôle source plug-in DLL:

- Trouvez le plug-in par défaut de contrôle des sources et connectez-vous silencieusement.

- Trouvez tous les plug-ins de contrôle source enregistrés, à partir desquels l’utilisateur en choisit un.

  Pour localiser le DLL de la première façon, l’IDE regarde sous le **HKEY_LOCAL_MACHINE-Software-SourceCodeControlProvider** subkey pour l’entrée **ProviderRegKey**. La valeur de cette entrée indique un autre sous-clé. L’IDE cherche alors une entrée nommée **SccServerPath** dans ce deuxième sous-clé sous **HKEY_LOCAL_MACHINE**. La valeur de cette entrée indique l’IDE au DLL.

> [!NOTE]
> L’IDE ne charge pas les DLL à partir de chemins relatifs (par exemple, *.- NewProvider.DLL*). Un chemin complet vers le DLL doit être spécifié (par exemple, *c: 'Providers’NewProvider.DLL*). Cela renforce la sécurité de l’IDE en empêchant le chargement de DLL plug-in non autorisés ou imités.

 Pour localiser le DLL de la deuxième façon, l’IDE regarde sous le **HKEY_LOCAL_MACHINE-Software-SourceCodeControlProvider-InstalledSCCProviders** subkey pour toutes les entrées. Chaque entrée a un nom et une valeur. L’IDE affiche une liste de ces noms à l’utilisateur. Lorsque l’utilisateur choisit un nom, l’IDE trouve la valeur du nom sélectionné qui indique un sous-clé. L’IDE cherche une entrée nommée **SccServerPath** dans ce sous-clé sous **HKEY_LOCAL_MACHINE**. La valeur de cette entrée indique l’IDE au DLL correct.

 Un plug-in de contrôle source doit prendre en charge les deux façons de trouver le DLL et, par conséquent, définit **ProviderRegKey**, la sur-rédaction de tout paramètre précédent. Plus important encore, il doit s’ajouter à la liste des **installateurs** afin que l’utilisateur puisse avoir le choix de quel plug-in de contrôle source à utiliser.

> [!NOTE]
> Étant donné que la **clé HKEY_LOCAL_MACHINE** est utilisée, un seul plug-in de contrôle source peut être [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enregistré comme plug-in de contrôle source par défaut sur une machine donnée (cependant, permet aux utilisateurs de déterminer quel plug-in de contrôle source qu’ils veulent réellement utiliser pour une solution particulière). Pendant votre processus d’installation, vérifiez si un plug-in de contrôle source est déjà réglé ; Si c’est le cas, demandez à l’utilisateur s’il faut ou non définir le nouveau plug-in de contrôle source en cours d’installation comme par défaut. Pendant la non-réinstallation, ne supprimez pas d’autres sous-clés de registre qui sont communes à tous les plug-ins de contrôle de source dans **HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider**; supprimer uniquement votre sous-clé SCC particulière.

## <a name="how-the-ide-detects-version-1213-support"></a>Comment l’IDE détecte la version 1.2/1.3 support
 Comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détecte-t-il si un plug-in prend en charge la version plug-in source Control API 1.2 et 1.3 fonctionnalités? Pour déclarer la capacité avancée, le plug-in de contrôle source doit implémenter la fonction correspondante :

 Tout [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] d’abord, vérifie la valeur retournée en appelant le [SccGetVersion](../../extensibility/sccgetversion-function.md). Il doit être supérieur ou égal à 1,2.

 Ensuite, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détermine si la nouvelle capacité particulière `lpSccCaps` est étayée par l’examen de l’argument sur la [SccInitialize](../../extensibility/sccinitialize-function.md).

 Si ces deux conditions sont remplies, les nouvelles fonctions prises en charge dans les versions 1.2 et 1.3 peuvent être appelées.

## <a name="see-also"></a>Voir aussi
- [Démarrer avec des plug-ins de contrôle de source](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
