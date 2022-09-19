# Starting from an official AWS image
# Keep any dependencies and versions in this file aligned with the environment.yml and Makefile
FROM public.ecr.aws/lambda/python:3.7

# Install Python dependencies
COPY requirements/prod.txt ./requirements.txt
RUN pip install --upgrade pip==21.1.3 --target "${LAMBDA_TASK_ROOT}"
RUN pip install -r requirements.txt --target "${LAMBDA_TASK_ROOT}"

# Copy only the relevant directories and files
#   note that we use a .dockerignore file to avoid copying logs etc.
COPY text_recognizer/ ./text_recognizer ${LAMBDA_TASK_ROOT}
COPY api.py ./ ${LAMBDA_TASK_ROOT}

CMD ["api.handler"]
