# 📊 Grafana Dashboards

A single source‑of‑truth repository for all dashboards that power my primary Grafana instance.  
The dashboards are automatically provisioned into Grafana via the **GitSync** feature, so any change you push to this repo is reflected in your Grafana UI within seconds.

> **TL;DR** – Clone → Edit → Commit → Push. GitSync takes care of the rest.

---

## Table of Contents

- [📊 Grafana Dashboards](#-grafana-dashboards)
  - [Table of Contents](#table-of-contents)
  - [Why this repo?](#why-this-repo)
  - [Folder structure](#folder-structure)
  - [Adding / updating dashboards](#adding--updating-dashboards)
    - [Exporting from Grafana](#exporting-from-grafana)
    - [Importing into GitSync](#importing-into-gitsync)
  - [GitSync workflow](#gitsync-workflow)
    - [Commit \& push](#commit--push)
    - [Automatic provisioning](#automatic-provisioning)
  - [Contributing](#contributing)
    - [Checklist](#checklist)
  - [License](#license)
  - [Resources](#resources)

---

## Why this repo?

* **Single source of truth** – All dashboards are version‑controlled and auditable.
* **Rapid roll‑out** – GitSync pushes changes to Grafana in real time, no manual re‑import required.
* **Collaboration** – Team members can review, comment and merge changes via pull requests.
* **Backup & restore** – The repo is a full backup of every dashboard JSON.

---

## Folder structure

```
├── dashboards/
│   ├─ folder-a/
│   │   └─ my-app-dashboard.json
│   ├─ folder-b/
│   │   └─ my-app-dashboard-staging.json
│   └─ folder-c/
│       └─ common-metrics.json
├── README.md
└── .gitignore
```

Feel free to add more sub‑folders as your environment grows.

---

## Adding / updating dashboards

### Exporting from Grafana

1. Open the dashboard you want to export.
2. Click **Share** → **Export** → **Save to file**.
3. Save the JSON file into the appropriate folder (`folder-a/`, `folder-b/`, or `folder-c/`).

### Importing into GitSync

*If you already have the dashboard in Grafana:*

1. **Delete** it from the UI (to avoid duplicate IDs).  
2. Commit and push the JSON file to this repo.

*If you are creating a new dashboard:*

1. Create a new JSON file in the correct folder.
2. Commit and push.

> **Tip** – Use a consistent naming convention:  
> `appname-environment-dashboard.json` (e.g., `webserver-production.json`).

---

## GitSync workflow

### Commit & push

```bash
git add dashboards/production/my-app-dashboard.json
git commit -m "Add new production dashboard for WebApp"
git push origin main
```

### Automatic provisioning

GitSync watches the `dashboards/` directory in your Grafana instance.  
When it detects a change:

1. It pulls the new JSON.
2. Creates or updates the dashboard in Grafana.
3. Logs the action to the **GitSync** panel for auditability.

All of this happens in < 10 seconds.

---

## Contributing

We welcome contributions! Please follow these guidelines:

1. Fork the repo and create a feature branch.
2. Add your dashboard JSON to the appropriate folder.
3. Run `git diff --name-only` to confirm only the intended files changed.
4. Submit a pull request with a clear description of what you added/updated.

### Checklist

- ✅ Dashboard JSON is valid (Grafana will reject invalid files).
- ✅ Dashboard name and folder are consistent with the naming convention.
- ✅ No sensitive data (API keys, passwords) is included in the JSON.

---

## License

MIT © [Supporterino](https://github.com/Supporterino)

> Feel free to use, modify, and distribute these dashboards under the MIT license.

---

## Resources

| Topic | Link |
|-------|------|
| GitSync documentation | https://grafana.com/docs/grafana/latest/observability-as-code/provision-resources/intro-git-sync/ |
| Grafana dashboard JSON format | https://grafana.com/docs/grafana/latest/dashboards/json-model/ |
| Grafana best practices | https://grafana.com/docs/grafana/latest/dashboards/best-practices/ |

--- 

Happy monitoring! 🚀