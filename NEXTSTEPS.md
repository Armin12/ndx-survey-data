# Next Steps for ndx-survey-data Extension for NWB:N

## Creating Your Extension

1. In a terminal, change directory into the new ndx-survey-data directory.

2. Add any packages required by your extension to `requirements.txt` and `setup.py`.

3. Run `python -m pip install -r requirements.txt` to install the `pynwb` package
and any other packages required by your extension.

4. Modify `src/create_extension_spec.py` to define your extension.

    - If you want to create any custom classes for interacting with the extension,
      add them to the `src/pynwb`.
      - If present, the `src/pynwb` folder MUST contain the following:
        - `ndx-survey-data` - Folder with the sources of the NWB extension
        - `ndx-survey-data/__init__.py` - Python file that may be empty
        - `requirements.txt` - Text file listing the Python package requirements for the extension
        - `README.md` - Markdown file describing the NWB extension
      - If present, the `src/pynwb` folder MAY contain the following files/folders:
        - `test` - Folder for unit tests for the extensions
        - `jupyter_widgets` - Optional package with custom widgets for use with Jupyter

5. Run `python src/spec/create_extension_spec.py` to generate the
`spec/ndx-survey-data.namespace.yaml` and
`spec/ndx-survey-data.extensions.yaml` files.

6. You may need to modify `setup.py` and re-run `python setup.py install` if you
use any dependencies.


## Documenting and Publishing Your Extension to the Community

1. Clone the latest nwb-docutils repository https://github.com/nwb-extensions-test/ndx-template.git
or install the latest release:
`python -m pip install nwb-docutils`
    - If you cloned the latest version, run `python setup.py install` to install nwb-docutils locally.

2. Start a git repository for your extension directory ndx-survey-data
 and push it to GitHub. You will need a GitHub account.
    - Follow these directions:
  https://help.github.com/en/articles/adding-an-existing-project-to-github-using-the-command-line

3. Change directory into `docs`.

4. Run `make html` to generate documentation for your extension based on the YAML files.

5. Read `docs/README.md` for instructions on how to customize documentation for
your extension.

6. Modify `README.md` to describe this extension for interested developers.

7. Add a license file. Permissive licenses should be used if possible. **A [BSD license](https://opensource.org/licenses/BSD-3-Clause) is recommended.**

8. Make a release for the extension on GitHub with the version number specified. e.g. if version is 0.1.0, then this page should exist: https://github.com/armin12/ndx-survey-data/releases/tag/0.1.0 . For instructions on how to make a release on GitHub see [here](https://help.github.com/en/github/administering-a-repository/creating-releases).

9. Publish your updated extension on PyPi.
    - Follow these directions: https://packaging.python.org/tutorials/packaging-projects/
    - You may need to modify `setup.py`
    - If your extension version is 0.1.0, then this page should exist: https://pypi.org/project/ndx-survey-data/0.1.0

   Once your GitHub release and ``setup.py`` are ready, publishing on PyPI:
    ```bash
    python setup.py sdist bdist_wheel
    twine upload dist/*
    ```

10. Go to https://github.com/nwb-extensions/staged-extensions and fork the
repository.

11. Clone the fork onto your local filesystem.

12. Copy the directory `staged-extensions/example` to a new directory
`staged-extensions/ndx-survey-data`:

    ```bash
    cp -r staged-extensions/example staged-extensions/ndx-survey-data
    ```

13. Edit `staged-extensions/ndx-survey-data/ndx-meta.yaml`
with information on where to find your NWB extension.
    - The YAML file MUST contain a dict with the following keys:
      - name: extension namespace name
      - version: extension version
      - src: URL for the main page of the public repository (e.g. on GitHub, BitBucket, GitLab) that contains the sources of the extension
      - pip: URL for the main page of the extension on PyPI
      - license: name of the license of the extension
      - maintainers: list of GitHub
      usernames of those who will reliably maintain the extension
    -

  You may copy and modify the following YAML that was auto-generated:
```yaml
name: ndx-survey-data
version: 0.1.0
src: https://github.com/armin12/ndx-survey-data
pip: https://pypi.org/project/ndx-survey-data/
license: BSD 3-Clause
maintainers:
  - bendichter
```

14. Edit `staged-extensions/ndx-survey-data/README.md`
to add information about your extension. You may copy it from
`ndx-survey-data/README.md`.

  ```bash
cp ndx-survey-data/README.md staged-extensions/ndx-survey-data/README.md
```

15. Add and commit your changes to Git and push your changes to GitHub.
```
cd staged-extensions
git add ndx-survey-data
git commit -m "Add new catalog entry for ndx-survey-data" .
git push
```

16. Open a pull request. Building of your extension will be tested on Windows,
Mac, and Linux. The technical team will review your extension shortly after
and provide feedback and request changes, if any.

17. When your pull request is merged, a new repository, called
ndx-survey-data-feedstock will be created in the nwb-extensions
GitHub organization and you will be added as a maintainer for that repository.


## Updating Your Published Extension

1. Update your ndx-survey-data GitHub repository.

2. Publish your updated extension on PyPI.

3. Fork the ndx-survey-data-feedstock repository on GitHub.

4. Open a pull request to test the changes automatically. The technical team
will review your changes shortly after and provide feedback and request changes,
 if any.

5. Your updated extension is approved.
