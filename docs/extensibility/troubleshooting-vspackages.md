---
title: Dépannage VSPackages (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698914"
---
# <a name="troubleshooting-vspackages"></a>Dépannage de VSPackages
Voici les problèmes courants que vous pourriez avoir avec votre VSPackage et des conseils pour résoudre les problèmes.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Pour dépanner un VSPackage qui empêche Visual Studio de démarrer

- Commencez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en mode sans échec.

   Pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] commencer en mode sans échec, à une invite de commande, type **devenv.exe /safemode**.

   Au cours de ce processus, aucun VSPackages ne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sont chargés, sauf les VSPackages qui sont inclus avec .

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Pour dépanner un VSPackage qui ne se charge pas

1. Assurez-vous que vous utilisez la racine de registre dans laquelle le VSPackage est enregistré pour fonctionner, généralement la racine de registre expérimental.

    Pour plus d’informations, voir [The Experimental Instance](../extensibility/the-experimental-instance.md).

2. Si le VSPackage est destiné à fonctionner dans la racine de registre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]expérimental, assurez-vous que vous exécutez la version expérimentale de .

    Pour exécuter la version expérimentale, tapez ce qui suit dans une fenêtre de commande : **devenv/rootsuffix exp**.

3. Vérifiez vos inscriptions au registre VSPackage.

    Pour plus d’informations, voir [Enregistrement VSPackages](registering-and-unregistering-vspackages.md) et [Gestion VSPackages](../extensibility/managing-vspackages.md).

4. Ouvrez la fenêtre de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **sortie** de l’instance de ce qui ne parvient pas à charger le VSPackage. Les informations sur les raisons pour lesquelles le VSPackage ne se charge pas peuvent être affichées dans cette fenêtre.

   > [!NOTE]
   > Si vous commencez la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] version [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] expérimentale de l’environnement de développement intégré (IDE), inspectez la fenêtre **de sortie** des deux versions.

5. Examinez le journal d’activité.

    Pour plus d’informations, voir [Comment : Utilisez le journal d’activité](../extensibility/how-to-use-the-activity-log.md).

6. Pour plus d’informations sur les exceptions lancées par l’IDE, cliquez sur **Exceptions** sur le menu **Debug** pour activer les exceptions. Dans la boîte de dialogue **Exceptions** sélectionner les types d’exceptions sur lesquelles vous voulez plus d’informations.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Pour dépanner un VSPackage qui ne s’enregistre pas

1. Assurez-vous que l’assemblage VSPackage réside dans un endroit de confiance. RegPkg ne peut pas enregistrer les assemblages dans un emplacement non fiable ou partiellement fiable, comme une part de réseau dans la configuration de sécurité .net par défaut. Bien qu’un avertissement s’affiche chaque fois qu’un utilisateur crée un projet dans un endroit non fiable, la case à cocher « ne pas afficher ce message à nouveau » peut empêcher cet avertissement de se reproduire.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Pour dépanner une commande qui n’est pas visible ou qui génère une erreur lorsque vous cliquez sur une commande

1. Fusionner les commandes de menu nouvelles ou modifiées et celles déjà [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans l’IDE en tapant ce qui suit à la Commande Prompt: **devenv /rootsuffix Exp / configuration**.

2. Assurez-vous [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que peut trouver UI.dll pour votre VSPackage.

   1. Trouvez le CLSID du VSPackage dans la section Paquets du registre :

        Version studio HKLM-Software-Microsoft-Visual\\*\<>*'Packages'

   2. Vérifiez que le chemin donné par le sous-clé SatelliteDll est correct.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Pour dépanner un VSPackage qui se comporte de façon inattendue

1. Définissez les points d'arrêt dans votre code.

     Les bons points de départ pour le débogage sont le constructeur et la méthode d’initialisation. Vous pouvez également définir des points d’arrêt dans la zone que vous souhaitez évaluer, comme une commande de menu. Pour activer les points d’arrêt, vous devez courir sous le débailleur.

    1. Dans le menu **Projet** , cliquez sur **Propriétés**.

    2. Sur la boîte de dialogue **des Pages De Property,** sélectionnez l’onglet **Debug.**

    3. Dans la **boîte d’arguments de la ligne de commande,** tapez le suffixe racine de l’environnement de développement que vos cibles VSPackage. Par exemple, pour sélectionner la construction expérimentale, tapez: **/RootSuffix Exp**.

    4. Sur le menu **Debug,** cliquez sur **Démarrer Debugging** ou appuyez sur F5.

        > [!NOTE]
        > Si vous débogagez un projet, créez ou chargez une instance existante de votre projet dès maintenant.

2. Utilisez le journal d’activité.

     Tracez le comportement VSPackage en écrivant des informations au journal d’activité à des points clés. Cette technique est particulièrement utile lorsque vous exécutez un VSPackage dans un environnement de vente au détail. Pour plus d’informations, voir [Comment : Utilisez le journal d’activité](../extensibility/how-to-use-the-activity-log.md).

3. Utilisez des symboles publics.

     Pour améliorer la lisibilité tout en débogage, vous pouvez attacher des symboles au débogage.

    1. Du menu **Outils/Options,** naviguez jusqu’à la boîte de dialogue **Debugging/Symbols.**

    2. Ajouter cet **emplacement de fichier Symbol (.pdb)**:

         `https://msdl.microsoft.com/download/symbols`

    3. Pour améliorer les performances, spécifiez un dossier de cache de symbole, par exemple :

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Pour dépanner un VSPackage manquant ou l’une de ses dépendances

1. Pour le code géré, assurez-vous que les chemins de référence sont corrects.

   1. Dans le menu **Projet** , cliquez sur **Propriétés**.

   2. Sélectionnez l’onglet **Références** dans la boîte de dialogue **des Pages De propriété** et assurez-vous que tous les chemins sont corrects. Vous pouvez également utiliser le **navigateur d’objets** pour parcourir les objets référencés.

        Pour le code géré, vous pouvez utiliser le [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) pour afficher les détails des charges d’assemblage échouées.

2. Pour obtenir du code non gémandé, trouvez le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID du VSPackage dans le nœud de registre CLSID :

    Version studio HKLM-Software-Microsoft-Visual\\*\<>*'CLSID'

   Assurez-vous que l’entrée InprocServer32 a le bon chemin de la dll VSPackage.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)
