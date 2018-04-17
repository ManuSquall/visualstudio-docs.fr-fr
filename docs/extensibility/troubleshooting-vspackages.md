---
title: Dépanner les packages VS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73c754de72238671dd10235e792c43fb6d0a1b5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-vspackages"></a>Dépanner les packages VS
Voici les problèmes courants que vous pouvez avoir avec votre VSPackage et conseils pour résoudre les problèmes.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Pour résoudre les problèmes d’un VSPackage qui empêche le démarrage de Visual Studio  
  
-   Démarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en mode sans échec.  
  
     Pour démarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en mode sans échec, à l’invite de commandes, tapez **devenv.exe /safemode**.  
  
     Pendant ce processus aucun VSPackages ne sont chargées, sauf les VSPackages sont incluses avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Pour résoudre les problèmes d’un VSPackage qui ne se charge pas  
  
1.  Assurez-vous que vous utilisez la racine du Registre dans laquelle le VSPackage est inscrit à exécuter, généralement la racine du Registre expérimentale.  
  
     Pour plus d’informations, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
2.  Si le VSPackage est ciblé pour s’exécuter dans la racine du Registre expérimentale, assurez-vous que vous exécutez la version expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Pour exécuter la version expérimentale, tapez la commande suivante dans une fenêtre de commande : **devenv/rootsuffix exp**.  
  
3.  Vérifiez les entrées de Registre du VSPackage.  
  
     Pour plus d’informations, consultez [l’inscription de VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) et [la gestion des VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Ouvrez le **sortie** fenêtre de l’instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui ne peut pas charger le VSPackage. Informations sur la raison pour laquelle le package Visual Studio ne peut pas charger peuvent être affichées dans cette fenêtre.  
  
    > [!NOTE]
    >  Si vous démarrez la version expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE), inspecter la **sortie** fenêtre des deux versions.  
  
5.  Examinez le journal d’activité.  
  
     Pour plus d’informations, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Pour plus d’informations sur les exceptions levées par l’IDE, cliquez sur **Exceptions** sur la **déboguer** menu Activer les exceptions. Dans le **Exceptions** boîte de dialogue Sélectionner les types d’exceptions sur lequel vous souhaitez plus d’informations.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Pour résoudre les problèmes d’un VSPackage qui n’a pas été inscrit  
  
1.  Assurez-vous que l’assembly VSPackage réside dans un emplacement approuvé. RegPkg ne peut pas inscrire des assemblys dans un emplacement non approuvé ou niveau de confiance partiel, tel qu’un partage réseau dans la configuration de sécurité par défaut .net. Bien qu’un avertissement s’affiche chaque fois qu’un utilisateur crée un projet dans un emplacement non approuvé, la case à cocher « ne plus afficher ce message » peut empêcher cet avertissement ne se reproduisent.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Pour résoudre les problèmes d’une commande qui n’est pas visible, ou qui génère une erreur lorsque vous cliquez sur une commande  
  
1.  Fusionner les commandes de menu Nouveau ou modifié et ceux déjà dans l’IDE en tapant ce qui suit à le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] invite de commandes : **/rootsuffix de devenv /setup de Exp**.  
  
2.  Assurez-vous que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] trouverez UI.dll pour votre VSPackage.  
  
    1.  Rechercher le CLSID du VSPackage dans la section des Packages du Registre :  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<version >*\Packages  
  
    2.  Vérifiez que le chemin d’accès fourni par la sous-clé SatelliteDll est correct.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Pour résoudre les problèmes d’un VSPackage qui se comporte de manière inattendue  
  
1.  Définissez les points d'arrêt dans votre code.  
  
     Bons points de départ pour le débogage sont le constructeur et la méthode d’initialisation. Vous pouvez également définir des points d’arrêt dans la zone que vous souhaitez évaluer, telle qu’une commande de menu. Pour activer les points d’arrêt, vous devez exécuter sous le débogueur.  
  
    1.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
    2.  Sur le **Pages de propriétés** boîte de dialogue, sélectionnez le **déboguer** onglet.  
  
    3.  Dans le **arguments de ligne de commande** , tapez le suffixe de la racine de l’environnement de développement qui les cibles de votre VSPackage. Par exemple, pour sélectionner la build expérimentale, tapez : **RootSuffix Exp**.  
  
    4.  Sur le **déboguer** menu, cliquez sur **démarrer le débogage** ou appuyez sur F5.  
  
        > [!NOTE]
        >  Si vous déboguez un projet, créez ou dorénavant d’une instance existante de votre projet.  
  
2.  Utilisez le journal d’activité.  
  
     Suivre les comportements de VSPackage en écrivant des informations dans le journal d’activité à des points clés. Cette technique est particulièrement utile lorsque vous exécutez un VSPackage dans un environnement de détail. Pour plus d’informations, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Utilisez les symboles publics.  
  
     Pour améliorer la lisibilité lors du débogage, vous pouvez joindre des symboles pour le débogueur.  
  
    1.  À partir de la **Outils/Options** menu, accédez à la **débogage/symboles** boîte de dialogue.  
  
    2.  Ajoutez ceci **emplacement du fichier (.pdb) de symboles**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Pour améliorer les performances, spécifiez un dossier de cache de symboles, par exemple :  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Pour résoudre les problèmes d’un VSPackage manquant ou une de ses dépendances  
  
1.  Pour le code managé, assurez-vous que les chemins d’accès de référence sont corrects.  
  
    1.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
    2.  Sélectionnez le **références** onglet dans le **Pages de propriétés** boîte de dialogue et assurez-vous que tous les chemins sont corrects. Vous pouvez également utiliser le **Explorateur d’objets** pour rechercher les objets référencés.  
  
         Pour le code managé, vous pouvez utiliser la [Fuslogvw.exe (Visionneuse Journal de liaison d’Assembly)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) pour afficher les détails des chargements d’assemblys ayant échoué.  
  
2.  Du code non managé, rechercher le CLSID du VSPackage dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nœud de Registre CLSID :  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<version >*\CLSID  
  
 Assurez-vous que l’entrée InprocServer32 a le chemin d’accès correct de la dll du VSPackage.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)