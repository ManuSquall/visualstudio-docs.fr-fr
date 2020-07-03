---
title: 'Procédure : utiliser le journal d’activité | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 824feee64f928dc837a379aeb539daaa5ba0d1db
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905588"
---
# <a name="how-to-use-the-activity-log"></a>Procédure : utiliser le journal d’activité
Les VSPackages peuvent écrire des messages dans le journal d’activité. Cette fonctionnalité est particulièrement utile pour déboguer les VSPackages dans les environnements de vente au détail.

> [!TIP]
> Le journal d’activité est toujours activé. Visual Studio conserve une mémoire tampon enchaînée des 100 dernières entrées, ainsi que les 10 premières entrées, qui contiennent des informations de configuration générales.

## <a name="to-write-an-entry-to-the-activity-log"></a>Pour écrire une entrée dans le journal d’activité

1. Insérez ce code dans la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode ou dans toute autre méthode, à l’exception du constructeur VSPackage :

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Ce code obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service et le convertit en une <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>écrit une entrée d’information dans le journal d’activité à l’aide du contexte culturel actuel.

2. Lorsque le VSPackage est chargé (généralement lorsqu’une commande est appelée ou qu’une fenêtre est ouverte), le texte est écrit dans le journal d’activité.

## <a name="to-examine-the-activity-log"></a>Pour examiner le journal d’activité

1. Exécutez Visual Studio avec le commutateur de ligne de commande [/log](../ide/reference/log-devenv-exe.md) pour écrire des ActivityLog.xml sur le disque au cours de votre session.

2. Après la fermeture de Visual Studio, recherchez le journal d’activité dans le sous-dossier pour les données Visual Studio :

   <em> *% AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*.

3. Ouvrez le journal d’activité avec n’importe quel éditeur de texte. Voici une entrée typique :

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programmation fiable

Étant donné que le journal d’activité est un service, le journal d’activité n’est pas disponible dans le constructeur VSPackage.

Vous devez obtenir le journal d’activité juste avant de l’écrire. Ne mettez pas en cache ou n’enregistrez pas le journal d’activité pour une utilisation ultérieure.

## <a name="see-also"></a>Voir aussi

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Dépannage de VSPackages](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
