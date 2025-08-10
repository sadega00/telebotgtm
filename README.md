with open(os.path.join(project_name, "main.py"), "w") as f:
    f.write(main_py)

with open(os.path.join(project_name, "requirements.txt"), "w") as f:
    f.write(requirements_txt)

with open(os.path.join(project_name, "Procfile"), "w") as f:
    f.write(procfile)

with open(os.path.join(project_name, "README.md"), "w") as f:
    f.write(readme_md)

# Membuat ZIP
zip_path = f"/mnt/data/{project_name}.zip"
with zipfile.ZipFile(zip_path, 'w') as zipf:
    for root, dirs, files in os.walk(project_name):
        for file in files:
            zipf.write(os.path.join(root, file),
                       os.path.relpath(os.path.join(root, file), project_name))

zip_path
