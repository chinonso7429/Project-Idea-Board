** start of script.js **

const projectStatus = {
  PENDING: {
    description: "Pending Execution"
  },
  SUCCESS: {
    description: "Executed Successfully"
  },
  FAILURE: {
    description: "Execution Failed"
  }
};
class ProjectIdea{
  constructor(title,description){
  this.title=title;
  this.description=description;
 this.status = projectStatus.PENDING }
 updateProjectStatus(newStatus) {
    if (
      newStatus === projectStatus.PENDING ||
      newStatus === projectStatus.SUCCESS ||
      newStatus === projectStatus.FAILURE
    ) {
      this.status = newStatus;
    } else {
      throw new Error("Invalid project status.");
    }
  }

}
class ProjectIdeaBoard {
  constructor(title) {
    this.title = title;
    this.ideas = [];
  }

  pin(projectIdea) {
    if (projectIdea instanceof ProjectIdea) {
      this.ideas.push(projectIdea);
    } else {
      throw new Error("Only instances of ProjectIdea can be pinned.");
    }
  }

  unpin(projectIdea) {
    const index = this.ideas.indexOf(projectIdea);
    if (index !== -1) {
      this.ideas.splice(index, 1);
    }
  }

  count() {
    return this.ideas.length;
  }

  formatToString() {
    let result = `${this.title} has ${this.ideas.length} idea(s)\n`;

    for (let idea of this.ideas) {
      result += `${idea.title} (${idea.status.description}) - ${idea.description}\n`;
    }

    return result;
  }
}


** end of script.js **

