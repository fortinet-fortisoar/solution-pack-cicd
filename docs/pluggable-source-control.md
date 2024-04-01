|[Home](../README.md)|
|--------------------|

# Creating Pluggable Source Control for Continuous Delivery

*Pluggable* source control uses the playbooks contained within installed source control connectors to perform a myriad of **Git** operations like:

- Adding members to a repository
- Cloning a repository
- Creating an issue
- Creating merge/pull request
- Creating a repository
- Creating a repository branch

## Requirements

Following rules serve as a guide for building *Pluggable* source control:

- The source control connector must have following information within `info.json`:

    - A category `Source Code Management`
    - A configuration parameter `username`

- The pluggable source control playbooks must be in the respective connector's sample playbook collection.

-  The pluggable playbook names must be in the format: `SourceControlName - OperationName`. For example, a pluggable playbook that *creates a repository* within the source control platform *GitLab* must have the name: _`GitLab - Create Repository`_.

-  The pluggable playbooks must have the tag in the format `SourceControlName-OperationName`. For example, a pluggable playbook that *creates a repository* within the source control platform *GitLab* must have the tag: _`GitLab-CreateRepository`_ (**no space**).

- The start step of all pluggable source control playbooks must be a *Referenced Step*. For information on creating a *Referenced* playbook step, refer to the section [Referenced Triggers](https://docs.fortinet.com/document/fortisoar/7.4.3/playbooks-guide/784146/triggers-steps#/document/fortisoar/7.4.3/playbooks-guide/784146/triggers-steps#Referenced) in FortiSOAR product documentation.

- The pluggable source control playbooks must be in an *Active* state. For information on marking a playbook as active, refer to the section [Creating Playbooks](https://docs.fortinet.com/document/fortisoar/7.4.3/playbooks-guide/331279/introduction-to-playbooks#/document/fortisoar/7.4.3/playbooks-guide/331279/introduction-to-playbooks#Creating_Playbooks) in FortiSOAR product documentation.

- The pluggable source control playbooks must accept two input parameters: 

    - `connector_config_id` which is a connector configuration ID

    - `dict_parameter` which contains connector action parameters
    
    View the **Parameter Name** and **Parameter Values** of `dict_parameter` for various pluggable source control playbooks in the following table:

<table>
    <th>NOTE</th>
    <td>Parameters must be correctly mapped. Any additional parsing of values required by the specific source control must be performed in the respective connector's playbooks.</td>
</table>

<table>
    <tr>
        <th>Playbook Name</th>
        <th>Parameter Name</th>
        <th>Dictionary</th>
        <th>Playbook Tag</th>
        <th>Additional Information</th>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Add Pull Request Review</td>
        <td><code>add_pr_review_params</code></td>
        <td>
<pre>{
    "org_name": "",
    "repo_name": "",
    "pull_number": "",
    "state": ""
}</pre>
        </td>
        <td><em>SourceControlName</em>-AddPullRequestReview</td>
        <td>Adds a review to the specified pull request. </td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Update Issue</td>
        <td><code>update_issue_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "issue_no":"",
    "contents":"",
    "state":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-UpdateIssue</td>
        <td>Updates an issue and adds a comment using value specified in <code>contents</code>.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Create Issue</td>
        <td><code>create_issue_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "issue_title":"",
    "issue_content":"",
    "issue_assignee":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-CreateIssue</td>
        <td>Creates issue and adds comment specified in <code>issue_content</code>. Add a new key <code>number</code> in response and map it with the <code>iid</code> (GitLab only) field in the response.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - List Repository Issue</td>
        <td><code>list_repo_issues_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "state":"",
    "created_after":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-ListRepositoryIssue</td>
        <td>The last step of this playbook must be <em>Set Variable</em> step, where user must map the response of the <strong>List Repository Issue</strong> action with the following keys:
<pre>{ 
    "html_url": "", 
    "id": "", 
    "number": "", 
    "title": "", 
    "body": "", 
    "reporterUsername": "", 
    "assigneeUsername": "", 
    "state": "", 
    "repository_url": "", 
    "id": ""
}</pre>
        </td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Create Issue Comment</td>
        <td><code>add_issue_comment_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "cr_number":"",
    "commit_message":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-CreateIssueComment</td>
        <td>Creates an issue comment specified in <code>commit_message</code></td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Create Repository</td>
        <td><code>create_repo_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-CreateRepository</td>
        <td>Creates a repository and the <em>Create Repository</em> step must be set to <code>Ignore Error Yes</code>.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Create Branch</td>
        <td><code>create_branch_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "new_branch":"",
    "branch_name":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-CreateBranch</td>
        <td>Creates a branch and the <em>Create Branch</em> step must be set to <code>Ignore Error Yes</code>.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - List Pull Request</td>
        <td><code>list_pr_params</code></td>
        <td>
<pre>{
    "org_name": "",
    "repo_name": "",
    "state": "",
    "pull_number": "",
}</pre>
        </td>
        <td><em>SourceControlName</em>-ListPullRequest</td>
        <td>The last step of this playbook must be <em>Set Variable</em> step, where user must map the response of the <strong>List Pull Request</strong> action with the following keys:
<pre>{ 
    "reviewer_names": ""
    "html_url": "",
    "body": "", 
    "reporterUsername": "",
    "assigneeUsername": "",
    "repository_url": "",
}</pre>
        </td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Create Release</td>
        <td><code>create_release_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "tag_name":"",
    "base_branch":"",
    "release_description":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-CreateRelease</td>
        <td>Create a release based on the specified parameters.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Delete Branch</td>
        <td><code>delete_branch_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "branch_name":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-DeleteBranch</td>
        <td>Deletes the specified branch.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Fetch Release</td>
        <td><code>fetch_release_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "release_name":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-FetchRelease</td>
        <td>The last step of this playbook must be <em>Set Variable</em> step, where user must returns the release matching the <code>release_name</code> key from input.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Add Reviewers for a Pull Request</td>
        <td><code>add_reviewers_for_pr_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "pull_number":"",
    "reviewers":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-PullRequestAddReviewers</td>
        <td>Adds reviewers to the specified pull request.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - List Pull Request Reviews</td>
        <td><code>list_pr_reviews_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "pull_number":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-ListPullRequestReviews</td>
        <td>Lists all reviews on a specified PR. Keep <em>Set Variable</em> as the last step of this playbook where the key <code>state</code> has values <code>APPROVED</code>, if the pull request can be merged, or <code>UNAPPROVED</code>, if the PR cannot be merged.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Create Pull Request</td>
        <td><code>create_pr_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "head_repo":"",
    "base_branch":"",
    "pr_title":"",
    "pr_comments":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-CreatePullRequest</td>
        <td>Creates a pull request. Set <em>Ignore Error</em> flag to the step <em>Create Pull Request</em> to handle the scenario where if pull request is already created, the <strong>Create Pull Request</strong> action fails. If the playbook step executes successfully, we need to add new keys <code>number</code> and <code>html_url</code> in response and map it with the <code>iid</code> (GitLab only) and <code>web_url</code> (GitLab only) fields from the responses.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Merge Pull Request</td>
        <td><code>merge_pr_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "pull_number":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-MergePullRequest</td>
        <td>Merges the specified pull/merge request.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - List Repository Collaborator</td>
        <td><code>list_repo_collaborator_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-ListRepositoryCollaborator</td>
        <td>Return a list of repository collaborators. Username of each collaborator must be in the login key. For example, if action returns list of users in <code>uname</code>, add a new key <code>login</code> in response and map it with the <code>username</code> field from the response.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Add Repository Collaborator</td>
        <td><code>add_repo_collaborator_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "username":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-AddRepositoryCollaborator</td>
        <td>Adds a collaborator to a specified repository.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Clone Repository</td>
        <td><code>clone_repo_params</code></td>
        <td>
<pre>{
    "org_name":"",
    "repo_name":"",
    "branch_name":"",
    "clone_as_zip":""
}</pre>
        </td>
        <td><em>SourceControlName</em>-CloneRepository</td>
        <td>Clones a repository and returns the path.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Get Server URL</td>
        <td>Not Required</td>
        <td>Not Required</td>
        <td><em>SourceControlName</em>-GetServerURL</td>
        <td>Returns a dictionary with the key <code>html_url</code> and its value.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Update Remote Repository</td>
        <td><code>update_remote_repo_params</code></td>
        <td>
<pre>{
    "file_iri":"",
    "clone_path":""
}</pre></td>
        <td><em>SourceControlName</em>-UpdateRemoteRepository</td>
        <td>Updates the contents to be pushed to remote repository in the <code>/tmp</code> folder.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Push Changes</td>
        <td><code>push_changes_params</code></td>
        <td>
<pre>{
    "org": "",
    "branch": "",
    "repo_type": "",
    "clone_path": "",
    "project_name": "",
    "commit_message": "",
    "commit_description": ""
}</pre>
        </td>
        <td><em>SourceControlName</em>-PushChanges</td>
        <td>Pushes the content updated in the <code>/tmp</code> folder to the source control repository.</td>
    </tr>
    <tr>
        <td><em>SourceControlName</em> - Create or Update File Content</td>
        <td><code>create_update_file_content_params</code></td>
        <td>
<pre>{
    "org_name": "",
    "file_name": "",
    "repo_name": "",
    "branch_name": "",
    "file_content": "",
    "commit_message": ""
}</pre>
</td>
        <td><em>SourceControlName</em>-CreateUpdateFileContent</td>
        <td>Creates or updates a file. If file exists, the <em>Create File</em> step fails hence an <code>Ignore Error Yes</code> flag helps update the file. Returns <code>Create File</code> step result and status after creating the file and returns <em>Update File</em> step result and status.</td>
    </tr>
</table>
