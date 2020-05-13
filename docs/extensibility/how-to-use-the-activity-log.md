---
title: 'Comment : Utilisez le journal d’activité Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710580"
---
# <a name="how-to-use-the-activity-log"></a>Comment : Utilisez le journal d’activité
VSPackages peut écrire des messages au journal d’activité. Cette fonctionnalité est particulièrement utile pour débogage VSPackages dans les environnements de vente au détail.

> [!TIP]
> Le journal d’activité est toujours activé. Visual Studio conserve un tampon de roulement des 100 dernières entrées ainsi que les 10 premières entrées, qui ont des informations de configuration générale.

## <a name="to-write-an-entry-to-the-activity-log"></a>Pour écrire une entrée dans le journal d’activité

1. Insérez <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> ce code dans la méthode ou dans toute autre méthode, sauf le constructeur VSPackage :

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Ce code <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> obtient le service et <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> le jette à une interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>écrit une entrée d’information dans le journal d’activités en utilisant le contexte culturel actuel.

2. Lorsque le VSPackage est chargé (généralement lorsqu’une commande est invoquée ou qu’une fenêtre est ouverte), le texte est écrit au journal d’activité.

## <a name="to-examine-the-activity-log"></a>Examiner le journal d’activité

1. Exécutez Visual Studio avec le commutateur de ligne de commande [/Log](../ide/reference/log-devenv-exe.md) pour écrire ActivityLog.xml au disque pendant votre session.

2. Après la fermeture de Visual Studio, trouvez le journal d’activité dans le sous-dossier pour les données Visual Studio :

   <em> *%AppData%</em>'Microsoft’VisualStudio\\\<version>'ActivityLog.xml*.

3. Ouvrez le journal d’activité avec n’importe quel éditeur de texte. Voici une entrée typique:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Programmation fiable

Étant donné que le journal d’activité est un service, le journal d’activité n’est pas disponible dans le constructeur VSPackage.

Vous devez obtenir le journal d’activité juste avant de l’écrire. Ne cachez pas ou n’enregistrez pas le journal d’activité pour une utilisation future.

## <a name="see-also"></a>Voir aussi

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Dépannage de VSPackages](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
